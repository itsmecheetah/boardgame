This repository is for organizing the board game I'm making. Feel free to take any inspiration from my process.

# Events
### Definition
Events occur every time a tile is discovered. *(See [.../Events/Template.json](BoardGame/Events/Template.json) for a template.)* Events often include interactions with settlers, resulting in loss or gain of certain stats/items, depending on the event.

### Identification
Events are given an English name for players to use, likely to be located at the top of the card in big text. However, an alternate name is given for board game design and easy management. This is referred to as the identifier, or ID. Each ID starts with a prefix. There are 5 prefixes, each for a different player to recieve in their event deck. Those prefixes are G, L, Y, J, and Q. The prefix is followed by a code from 000 to 999. Below are examples of event IDs.

| Prefix        | Code          |   |   | Result        |
| ------------- | ------------- |---|---| ------------- |
| G             | 012           |   |   | G012          |
| L             | 038           |   |   | L038          |
| Y             | 042           |   |   | Y042          |
| J             | 035           |   |   | J035          |
| Q             | 003           |   |   | Q003          |

# Incursions
### Definition
Incursions occur once players have made an accusation. *(See [.../Incursions/Template.json](BoardGame/Incursions/Template.json) for a template.)* Incursions have up to 2 pages of content describing the goals of the players. There is also a seperate version for the ghost. Each incursion has a new ruleset, abilities, and more.

### Identification
Incursions are given an English name for players to use, likely to be located at the top of the card in big text. However, there are two other names: One for board game design, and one for players to locate each incursion easier.

The name for board game design is referred to as the ID. It contains the prefix "K", followed by a number between 000 and 999. Examples below.

| Prefix        | Code          |   |   | Result        |
| ------------- | ------------- |---|---| ------------- |
| K             | 012           |   |   | K012          |
| K             | 038           |   |   | K038          |

# Items
### Definition
Items are acquired through events.. *(See [.../Items/Template.json](BoardGame/Items/Template.json) for a template.)* Items usually grant certain actions or abilities to their holder.

### Identification
Items are given an English name for players to use, likely to be located at the top of the card in big text. However, an alternate name is given for board game design and easy management. This is referred to as the identifier, or ID. All items start with a prefix "H". The prefix is followed by a code from 000 to 999. Below are examples of event IDs.

| Prefix        | Code          |   |   | Result        |
| ------------- | ------------- |---|---| ------------- |
| H             | 012           |   |   | H012          |
| H             | 038           |   |   | H038          |

# Settlers
### Definition
Settlers are non-player characters living in the village. Most events feature a settler, but all settlers also have their own card with lore, a description, and statistics. *(See [.../Settlers/Template.json](BoardGame/Settlers/Template.json) for a template.)* Some settlers have certain effects that take place when you're on the same tile as them.

### Identification
Settlers are given an English name for players to use, likely to be located at the top of their card in big text. However, an alternate name is given for board game design and easy management. This is referred to as the identifier, or ID. All Settlers start with a prefix "F". The prefix is followed by a code from 00 to 99. Below are examples of settler IDs.

| Prefix        | Code          |   |   | Result        |
| ------------- | ------------- |---|---| ------------- |
| F             | 12            |   |   | F12           |
| F             | 38            |   |   | F38           |

# Triggers
### Definition
Triggers are basically a weird sort of function. Each trigger can be "called", and has certain effects ranging from adding cards from purgatory to a certain deck, changing stats, etc. As far as the players know, triggers do not exist. They are simply for the benefit of board game development and easy tracking of stuff that happens. Triggers can be called multiple ways, multiple times, and have multiple effects. I think you get the idea. *(See [.../Triggers/Template.json](BoardGame/Triggers/Template.json) for a template.)*

Whenever an event, item, or other element of the board game want to do something (like add a card or deal damage or smt) they will call a trigger. And yes, this will be done in their .json files. In descriptions/lore or whatever. The JSON parsers will keep an eye out for the `<id>` and will replace it with trigger action text. For example, an event that could potentially call a trigger with the id "I389" or "I393" might look like this:

<details>
  <summary>Click to expand</summary>
  
  ```
  {"event": {
  "version": "1",
  "id": "G389",
  "access": [
    "Exploration",
  ],
  "content": {
    "name": "The Great JSON Parser",
    "lore": "Man fears the JSON parser more than it fears linker errors...",
    "description": [ 
      {
        "type": "body", 
        "format": ["italic","bold"], 
        "value": "JSON Parser is not happy."
      },
      {
        "type": "body",
        "color": "#ff0000", 
        "format": ["strikethrough","underline"],
        "value": "He lunges forward."
      },
      {
        "type": "roll", 
        "outcomes": [{
          "number": "0-4",
          "lore": "HE STABS YOU!",
          "description": "<I389>"
        },
        {
          "number": "5+",
          "lore": "YOU DODGE HIM!",
          "description":"<I393>"
        }
      ]
      }
    ]
  }
}}
```
</details>

### Identification
Triggers are given no English name, only an ID. All triggers start with a prefix "I", followed by a code between 000 and 999. Examples below.

| Prefix        | Code          |   |   | Result        |
| ------------- | ------------- |---|---| ------------- |
| I             | 012           |   |   | I012          |
| I             | 038           |   |   | I038          |


## License
This project is licensed under [CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/).  
