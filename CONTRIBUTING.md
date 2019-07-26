
# Development
Below are some global rules when it comes to editing the Emerald Gaming Files.

* [Colouring](./Development#colouring)
* [Variable Naming](./Development#variable-naming)
* [ElementData & EventHandlers](./Development#elementdata--eventhandlers)
* [Comments](./Development#comments)
* [Creating Commands](./Development#creating-commands)
* [Committing To GitHub](./Development#committing-to-github)

***

### Colouring
* All successful message colors are to be green. (0, 255, 0) | `0, 255, 0)`
* All error message colors are to be red. (255, 0, 0) | `255, 0, 0)`
* All informational/syntax preview colors are to be lime green. (75, 230, 10) | `75, 230, 10)`
* All roleplay line colors are to be light pink. (230, 25, 140) | `230, 25, 140)`

***

### Variable Naming
Variable names should be given the name of what they relatively hold.

* When using variables to store thePlayer, the variable must be called **thePlayer**.
* When using variables to store thePlayer's name, the variable must be called **thePlayerName**.

* When using variables to store the targetPlayer, the variable must be called **targetPlayer**.
* When using variables to store the targetPlayer's name, the variable must be called **targetPlayerName**.

***

### ElementData & EventHandlers
Naming event handlers and element data follow the same convection. the prefix should contain the resource name that it originates from or is primarily linked with, followed by a general name for what it does or is used for.

  * **ElementData Example:** *"hud:enabledstatus"* - used by the resource `hud-system` and saves the state of the HUD's enabled status.

  * **eventHandler Example:** *"character:spawnCharacter"* - Used by the resource `character-system` and triggers the spawning of the given character.

As seen above, the prefix is following the name of the resource, alongside a naming of what it generally does. The reason we follow this convection is to avoid naming eventHandlers and elementData the same across resources as it would conflict and cause issues.

For all ElementData, a entry in the [Saved Element Data](./Saved-Element-Data) page must be added in order to maintain a list of all data which exists.

***

### Comments
You should always leave comments every now and then within your code, especially in parts which may be hard to understand to make it easier for others and yourself to understand what is going on when checking over it later on in time.

If created a command, you must comment above the function name stating the primary command handler, it's parameters, who created it, the date of creation and what rank is required to use the command.


**Example:**
```
-- /sethp [Player/ID] [Health (1-100)] - by Skully (18/06/17) [Trial Admin]
function setPlayerHealth(thePlayer, commandName, targetPlayer, health)
...
```

***

### Creating Commands
When creating general commands, there are a few general things you must always check.
1. If there is more than one parameter in the command, make sure to check if the player has supplied everything needed for the command to execute correctly.
2. If the player needs to be logged in, make sure to check they are with elementData *"loggedin"*.
3. If the command executes on a target player, make sure to check if the target is also logged in.
4. If the command is for a staff member specifically, make sure you check for the players [rank](./Exported-Functions#s_stafflua-staff-related-functions).
5. If the command should only work when someone is not muted, use elementData `"account:muted"` to check.
6. Do you need to notify all staff members or all players of anything? [`exports.global:sendMessage()`](./Exported-Functions#s_functionslua-main-functions)
7. If the command should be logged, make sure you do so. [`exports.logs:addLog()`](./Exported-Functions#resource-logs-exportslogs)
8. If the command changes a player's data or content, notify the player of the change as required.
9. The command should generally also notify thePlayer regarding the status of it's execution. (Success messages, errors, etc.)
10. If it's an administrative command, should you notify managers of it being executed to catch administrative abuse? [`exports.global:sendMessageToManagers`](./Exported-Functions#s_messageslua-global-message-functions).

***

### Committing To GitHub
Prior to committing any code, ensure you have overlooked your code and there are no minor errors, typos or spelling mistakes as this would require you to commit once again, slowing the process of efficiency.

After your code is ready to go and you are prepared to push your code to the repository, the commit message should be relative to what your code involves. For example, if you were working on the command `/sethp`, your commit message would be *"/sethp added."*

* In the event that you are making adjustments to your code, you must use the name commit name as the original code's commit, and add a number afterwards incrementing upwards from 1. In this scenario, if we adjust the code for `/sethp` again, the commit message would be *"/sethp 2"*.

* If your commit is related to a issue, reference the issue within your commit message by using hashtag `#` followed by the ID of the issue.
  * **Example:** `/sethp (#15)`

* Ensure that you always update your [issue](../issues) throughout development. It's extremely important as it keeps others up to date on the current status of the issue and your work. Ensure the labels are correct and adjusted throughout the different stages of completion.
