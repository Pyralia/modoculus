# MODOCULUS Doc

///

# MongoDB Schema Documentation (SUMMARY)

## playerProfiles

| Field          | Type      | Description                                  |
| -------------- | --------- | -------------------------------------------- |
| _id            | String    | UUID of the player in .toString() format     |
| username       | String    | Username of the player                       |
| rank           | String    | Rank of the player                           |
| credits        | NumberInt | Credits of the player                        |
| discordId      | String    | Discord ID of the player, null if not linked |
| firstConnexion | String    | First connection date                        |
| lastConnexion  | String    | Last connection date                         |
| playTime       | NumberInt | Playtime in seconds                          |

## playerSubscriber

| Field                       | Type       | Description                                         |
| --------------------------- | ---------- | --------------------------------------------------- |
| _id                         | String     | UUID of the player in .toString() format            |
| subscriber.currentStage     | NumberInt  | Number of subscription months                       |
| subscriber.finishSubscriber | NumberLong | Timestamp when the subscription ends                |
| subscriber.prefix           | String     | Custom suffix (to be renamed from prefix to suffix) |
| subscriber.nextReward       | NumberLong | Timestamp for the next reward                       |

## gameHistory

| Field       | Type      | Description                                           |
| ----------- | --------- | ----------------------------------------------------- |
| _id         | String    | UUID of the game in .toString() format                |
| duration    | String    | Game duration formatted as "MM:ss"                    |
| date        | String    | Game date formatted as "dd/MM/yyyy MM:ss"             |
| winners     | [String]  | List of winner usernames                              |
| mumble      | Boolean   | Whether the game was on our mumble server             |
| private     | Boolean   | Whether the game was private (true) or public (false) |
| playerCount | NumberInt | Number of players at game start                       |
| host        | String    | Host's username                                       |
| scenarios   | [String]  | List of scenario names for the game                   |
| gamemode    | String    | Name of the game mode                                 |
| topKills    | [String]  | List of top 9 kills in the game                       |

## playersGameHistory

| Field    | Type      | Description                                                    |
| -------- | --------- | -------------------------------------------------------------- |
| _id      | String    | Combination of player UUID and game UUID in .toString() format |
| gameId   | String    | UUID of the game in .toString() format                         |
| playerId | String    | UUID of the player in .toString() format                       |
| kills    | NumberInt | Number of kills by the player                                  |
| diamonds | NumberInt | Number of diamonds mined by the player                         |
| golds    | NumberInt | Number of golds mined by the player                            |
| role     | String    | Role of the player ("Aucun" if none)                           |
| team     | String    | Team of the player ("Aucune" if none)                          |
| state    | String    | State of the player ("Vivant" if alive)                        |
| win      | Boolean   | Whether the player won the game (true) or not (false)          |

# MongoDB Schema Documentation (DETAILED)

This document outlines the MongoDB schema for our application, including the collections: `playerProfiles`, `playerSubscriber`, `gameHistory`, and `playersGameHistory`.

## Collection: playerProfiles

```json
{
  "_id": "String",          // UUID of the player in .toString() format
  "username": "String",     // Username of the player
  "rank": "String",         // Rank of the player
  "credits": "NumberInt",   // Credits of the player
  "discordId": "String",    // Discord ID of the player, null if Discord is not linked
  "firstConnexion": "String", // First connection date as a string
  "lastConnexion": "String", // Last connection date as a string
  "playTime": "NumberInt"   // Playtime in seconds
}
```

## Collection: playerSubscriber

```json
{
  "_id": "String",                        // UUID of the player in .toString() format
  "subscriber": {
    "currentStage": "NumberInt",          // Number of subscription months
    "finishSubscriber": "NumberLong",     // Timestamp when the subscription ends
    "prefix": "String",                   // Custom suffix (to be renamed from prefix to suffix)
    "nextReward": "NumberLong"            // Timestamp for the next reward
  }
}
```

## Collection: gameHistory

```json
{
  "_id": "String",                  // UUID of the game in .toString() format
  "duration": "String",             // Game duration formatted as "MM:ss"
  "date": "String",                 // Game date formatted as "dd/MM/yyyy MM:ss"
  "winners": ["String"],            // List of winner usernames
  "mumble": "Boolean",              // Whether the game was on our mumble server
  "private": "Boolean",             // Whether the game was private (true) or public (false)
  "playerCount": "NumberInt",       // Number of players at game start
  "host": "String",                 // Host's username
  "scenarios": ["String"],          // List of scenario names for the game
  "gamemode": "String",             // Name of the game mode
  "topKills": ["String"]            // List of top 9 kills in the game
}
```

## Collection: playersGameHistory

```json
{
  "_id": "String",                // Combination of player UUID and game UUID in .toString() format
  "gameId": "String",             // UUID of the game in .toString() format
  "playerId": "String",           // UUID of the player in .toString() format
  "kills": "NumberInt",           // Number of kills by the player
  "diamonds": "NumberInt",        // Number of diamonds mined by the player
  "golds": "NumberInt",           // Number of golds mined by the player
  "role": "String",               // Role of the player ("Aucun" if none)
  "team": "String",               // Team of the player ("Aucune" if none)
  "state": "String",              // State of the player ("Vivant" if alive)
  "win": "Boolean"                // Whether the player won the game (true) or not (false)
}