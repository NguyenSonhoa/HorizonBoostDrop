# HorizonBoostDrop

The HorizonBoostDrop plugin is designed to increase the drop rate of items from MythicMobs. It allows server owners to provide temporary or permanent boost rates to players, increasing their chances of obtaining valuable loot. The plugin supports both vanilla and MMOItems drops, with a configurable blacklist.

## Features

-   **Configurable Drop Amount Boost:** Grant players temporary or permanent percentage-based boosts to item drop amounts.
-   **MythicMobs Integration:** Specifically designed to work with drops from MythicMobs.
-   **MMOItems Support:** Boosts apply to MMOItems drops, with an option to blacklist specific items.
-   **Vanilla Item Support:** Boosts also apply to vanilla item drops, with an option to blacklist specific items.
-   **Permission-Based Boosts:** Players can receive additional boosts based on their permissions.
-   **Flexible Command System:** Comprehensive commands for managing boosts (add, remove, clear, list).
-   **PlaceholderAPI Support:** Display a player's current boost percentage using PlaceholderAPI.
-   **Persistent Boosts:** Boosts are saved and reloaded after a server restart.
-   **Customizable Messages:** All plugin messages can be configured through `messages.yml`.

## Installation

1.  Download the `HorizonBoostDrop.jar` file.
2.  Place the `HorizonBoostDrop.jar` file into your server's `plugins/` directory.
3.  (Optional) If you want PlaceholderAPI support, ensure PlaceholderAPI is also installed.
4.  Start or restart your server.
5.  The plugin will generate `config.yml` and `messages.yml` in `plugins/HorizonBoostDrop/`.

## Commands

All commands start with `/boostdrop` or its alias (if configured).

-   `/boostdrop help`: Displays the plugin's help message.
-   `/boostdrop <player> <seconds> <percent> [type] [source]`: Grants a temporary drop boost to a player.
    -   `<player>`: The target player's name.
    -   `<seconds>`: The duration of the boost in seconds.
    -   `<percent>`: The percentage increase in drop rate (e.g., `50` for +50%).
    -   `[type]`: (Optional) The type of boost (e.g., `COMMAND`, `EVENT`). Defaults to `COMMAND`.
    -   `[source]`: (Optional) A custom identifier for the boost (e.g., "Daily Reward"). Defaults to "Boosted by <sender_name>".
-   `/boostdrop addperm <player> <percent> [type] [source]`: Grants a permanent drop boost to a player.
    -   `<player>`: The target player's name.
    -   `<percent>`: The percentage increase in drop rate.
    -   `[type]`: (Optional) The type of boost. Defaults to `COMMAND`.
    -   `[source]`: (Optional) A custom identifier for the boost. Defaults to "Command by <sender_name>".
-   `/boostdrop list [player]`: Displays a summary of active boosts for a player. If no player is specified, it shows your boosts (if you are a player).
-   `/boostdrop remove <player> <source>`: Removes a specific boost from a player based on its source.
    -   `<player>`: The target player's name.
    -   `<source>`: The identifier of the boost to remove.
-   `/boostdrop clear <player>`: Removes all active boosts from a player.
-   `/boostdrop reload`: Reloads the plugin's configuration files (`config.yml` and `messages.yml`) and boost data.

## Permissions

-   `horizonboostdrop.admin`: Grants access to all administrative commands (`/boostdrop addperm`, `/boostdrop remove`, `/boostdrop clear`, `/boostdrop <player> <seconds> <percent>`).
-   `horizonboostdrop.reload`: Grants access to the `/boostdrop reload` command.
-   `horizonboostdrop.boost.<percent>`: Grants a static boost percentage to a player (e.g., `horizonboostdrop.boost.10` for a +10% boost). This boost is added to any active temporary/permanent boosts.

## Configuration (`config.yml`)

```yaml
# Main configuration for HorizonBoostDrop

# Blacklist of MMOItems that will not be boosted
# Format: <MMOItemType.ID> (e.g., SWORD.MYTHIC_SWORD)
blacklist:
  mmoitems:
    - "SWORD.MYTHIC_SWORD"
    - "ARMOR.LEGENDARY_CHESTPLATE"
  # Blacklist of vanilla items that will not be boosted
  # Format: <MATERIAL_NAME> (e.g., DIAMOND, STONE)
  vanilla:
    - "DIAMOND"
    - "STONE"

# Other settings may be added here in the future
```

## Configuration (`messages.yml`)

This file contains all user-facing messages, allowing for full customization.

Example:

```yaml
# Configuration messages for HorizonBoostDrop

no-permission: "&cYou do not have permission to execute this command."
player-not-found: "&cPlayer %player% not found."
invalid-number: "&cInvalid number."
invalid-type: "&cInvalid boost type. Valid types: COMMAND, EVENT, PERMISSION."
reload: "&aSuccessfully reloaded configuration and boost data!"

boost-applied:
  sender: "&aApplied &e+%percent% &aboost to &f%player% &aof type &b%type% &afor &e%time%."
  player: "&aYou have received a &e+%percent% &aboost of type &b%type% &afor &e%time%."
# ... (many other messages)
```

## PlaceholderAPI Support

If PlaceholderAPI is installed, you can use the following placeholders:

-   `%horizonboost_total%`, `%horizonboost_percent%`, `%horizonboost_total_percent%`: Displays the player's current total boost percentage.
-   `%horizonboost_time%`, `%horizonboost_remaining%`, `%horizonboost_time_left%`: Displays the longest remaining boost time in seconds.
-   `%horizonboost_time_formatted%`, `%horizonboost_remaining_formatted%`: Displays the longest remaining boost time formatted (e.g., "1h 30m", "45m 10s").
-   `%horizonboost_list%`, `%horizonboost_summary%`: Lists a summary of the player's active boosts.
-   `%horizonboost_count%`, `%horizonboost_amount%`: Displays the number of active boosts.
-   `%horizonboost_status%`, `%horizonboost_has_boost%`: Returns "yes" if the player has a boost, otherwise "no".
-   `%horizonboost_percent_raw%`: Displays the total boost percentage as an integer (without the % symbol).
-   `%horizonboost_top_percent%`: Displays the percentage of the highest active boost.
-   `%horizonboost_top_type%`: Displays the type of the boost with the highest percentage.
