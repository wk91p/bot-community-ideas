# bot-community-ideas

Community-driven ideas and feature suggestions for Highrise virtual reality bots.

This repository is intended as a simple place for the community to share ideas, improvements, and features they would like to see available for bots.

## Ideas

### Ideas credited to @UnbreakabIe

* **Message editing/deletion:** Allow bots to edit or delete messages. This would be useful for dynamic messages such as cooldowns, status updates, or other temporary information.
* **Increase WebSocket rate limits:** Increase the WebSocket rate limit slightly to improve stability in larger rooms, especially since the room capacity has been increased to 80 users.
* **More session_metadata details:** Provide additional information in `session_metadata`, such as the number of connected users, the bot's username, the owner's username, and the room's privileges.
* **get_room_privileges():** Add a `get_room_privileges()` method to allow bots to retrieve the current room privileges.
* **Bulk moderation actions:** Support performing moderation actions on multiple users with a single API request, such as muting multiple users at once.
* **Bulk whisper messages:** Add support for sending whisper messages to multiple users at once, which could be useful for hidden in-room announcements.
* **Typing indicator:** Add an indicator such as "Bot is typing...". Ideally, allow developers to control the displayed text and how long the indicator remains visible. This would provide a better user experience when an action is delayed or takes some time to complete.
* **Individual outfit item management:** `set_outfit()` currently replaces the entire outfit in a single operation. There is no way to add or remove an individual item without resending the entire outfit list. This requires developers to cache the complete outfit, which makes outfit management more difficult, especially for newer programmers.

### Ideas credited to @Blatant

* **Bot recommendation & advertising system:** It would be useful to have a recommendation system for discovering useful bots, or even a way for bot developers to purchase advertising, similar to the existing promotion system for worlds.
* **Bot trading:** It would be really cool if bots could create and accept trades. This could enable a lot of interesting features and systems to be built around trading, like creating a giveaway.
* **Profile & World moderation:** Allow bot owners to grant bots moderation permissions for their own profile or World profile. Bots could automatically remove inappropriate comments, detect spam, and reply to comments or World reviews. This could also enable AI-powered moderation and automated responses for popular Worlds.
* **Bot integration with personal DMs:** Allow users to connect a bot directly to their personal messages so the bot can receive and reply to incoming DMs on the user's behalf. The bot would effectively act as an assistant inside the user's inbox and could automatically answer people as if the replies were coming from the account owner.

### Ideas credited to @VECTOR000

* **Room design & construction:** Give bots access to the coordinates and placement of furniture in a room. This would let a bot copy an existing room's design or automatically rebuild a room from a saved layout.

```python
  # Get furniture positions, save as a template, then rebuild elsewhere
  items = await bot.highrise.get_room_furniture()
  template = [{"id": i.item_id, "x": i.x, "y": i.y, "z": i.z} for i in items]
  await bot.highrise.place_furniture(**template[0])
```

* **Profile backgrounds:** The SDK already lets a bot equip outfit items with `set_outfit()`, picking from free items or the bot's own inventory. Profile backgrounds could work the exact same way — a `set_profile_background()` call that takes a background item the bot owns or one that's free to use, just like outfit items work today.

* **Interactive command buttons:** In private messages, show commands as clickable buttons instead of typed text. Pressing a button triggers the command or shows its explanation.

* **Bot support for teams & groups:** Allow bots to join teams/groups and manage them — e.g. managing members, deleting messages, or blocking invites.

### Ideas credited to @Community

* **Interactive buttons & menus:** Bots should be able to send interactive buttons and menus to users. These could be used for:
  * Accept / Deny
  * Confirm / Cancel
  * Choose Red / Blue
  * Select a wager
  * Navigate to the next help page
  * Join a game
  * View balance

  *Example:*
  ```python
  await self.highrise.send_interactive_message(  
      "Accept @Community's 500g challenge?",  
      buttons=["Accept", "Deny"]  
  )
  ```

  These buttons could be sent directly to users or displayed on-screen, allowing bots to create polls, games, confirmations, and other interactive experiences.

* **Expanded moderation permissions:** With proper permission scopes, bots should be able to:
  * Temporarily mute users
  * Remove users from a room
  * Ban and unban users
  * Delete specific messages
  * Retrieve moderation status
  * Detect repeated spam
  * Read the room's moderator list
  * Apply slow mode

* **Private bot testing environment:** Developers should have a private environment where they can simulate events such as:
  * Users joining and leaving
  * Tips of different amounts
  * DMs
  * Movement
  * Disconnects
  * Duplicate events
  * Permission failures

  This would allow developers to safely test scenarios such as a 10,000g transaction without actually risking 10,000g.

* **Temporary interactive room objects:** Bots could temporarily spawn interactive objects for events and games, such as:
  * Game tables
  * Leaderboards
  * Signs
  * Prize wheels
  * Voting booths
  * Teleport pads
  * Countdown displays
  * Team markers

  These objects could automatically disappear when the event ends.

* **Interactive bot panels:** Bots should be able to display customizable interactive panels containing text, buttons, and dropdown menus.

  *Example:*
  ```python
  panel = BotPanel(  
      title="Community Casino",  
      private=True  
  )

  panel.add_text("Balance: 12,450g")  
  panel.add_button("Coinflip", action="open_coinflip")  
  panel.add_button("Slots", action="open_slots")  
  panel.add_button("Withdraw", action="open_withdrawal")  
  panel.add_dropdown("Wager", options=[100, 500, 1000, 5000])  

  await self.highrise.show_panel(user.id, panel)  
  ```

  This could provide a more flexible interface for games, utilities, menus, and other bot features without relying entirely on chat commands.

## Contributing

Have an idea for a feature that would improve bots?

Feel free to suggest it and include:

* A short title for the idea
* A description of the idea
* Why it would be useful
* Any possible use cases or examples
* Your username for credit

Please keep suggestions focused on bot functionality and explain the idea clearly enough for others to understand.

## Credits

Ideas in this repository are credited to the community members who originally suggested them.

If you contribute an idea, your username will be included alongside your suggestion.

---

**This is a community-driven list of ideas and suggestions. It does not represent a commitment that any feature will be implemented.**

Made with ❤️ by @UnbreakabIe

Discord: @oqs0_ | Highrise: @Unbreakable
