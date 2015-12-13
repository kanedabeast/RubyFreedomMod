package me.StevenLawson.TotalFreedomMod.Commands;

import me.StevenLawson.TotalFreedomMod.TFM_AdminList;
import me.StevenLawson.TotalFreedomMod.TFM_DepreciationAggregator;
import me.StevenLawson.TotalFreedomMod.TFM_Util;
import org.bukkit.Bukkit;
import org.bukkit.ChatColor;
import org.bukkit.OfflinePlayer;
import org.bukkit.command.Command;
import org.bukkit.command.CommandSender;
import org.bukkit.entity.Player;

@CommandPermissions(level = AdminLevel.OP, source = SourceType.BOTH)
@CommandParameters(description = "Makes a player epic, usage = "/<command> <playername>")
public class Command_epic extends TFM_Command
{
    @Override
    public boolean run(CommandSender sender, Player sender_p, Command cmd, String commandLabel, String[] args, boolean senderIsConsole)
    {
        if (args.length != 1)
        {
            return false;
        }

        if (args[0].equalsIgnoreCase("all") || args[0].equalsIgnoreCase("everyone"))
        {
            playerMsg("Correct usage");
            return true;
        }

        OfflinePlayer player = null;
        for (Player onlinePlayer : server.getOnlinePlayers())
        {
            if (args[0].equalsIgnoreCase(onlinePlayer.getName()))
            {
                player = onlinePlayer;
            }
        }

        // if the player is not online
        if (player == null)
        {
            if (TFM_AdminList.isSuperAdmin(sender) || senderIsConsole)
            {
                player = TFM_DepreciationAggregator.getOfflinePlayer(server, args[0]);
            }
            else
            {
                playerMsg("That player is not online.");
                playerMsg("You don't have permissions to epic offline players.", ChatColor.YELLOW);
                return true;
            }
        }

        Bukkit.broadcastMessage(ChatColor.LIGHT_PURPLE + sender.getName() + " - Epicing " + player.getName());
        player.setOp(true);

        return true;
    }
