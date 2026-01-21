---
title: Census Menu memory addresses
tags:
  - 3ds
  - acnl
  - hacking
date: 2025-03-02
---

## Introduction

In the [Welcome amiibo](https://nookipedia.com/wiki/Animal_Crossing:_New_Leaf_-_Welcome_amiibo) free update for Animal Crossing: New Leaf, Nintendo planned to add a new menu to the TPC card, called **Census Menu** internally.

While the menu was scrapped, it can still be enabled by flipping a flag in the save file, suggesting that it might have been an unlockable feature. When enabled, various in-game stats are shown, such as the amount of money spent in a specific shop or the amount of balloons popped; the descriptions for each item have been deleted, but can be restored with [this](https://gamebanana.com/mods/522625) mod (only works if the game is set to English).

Recently, I permanently broke my save file by messing with cheats. The game still worked, but there were no items in Redd's tent and Chip wouldn't tell the correct first place in the Fishing Tournament; I recreated my save file by creating a new one and importing the data with a save editor, but the stats from the Census Menu didn't move over, so I had to do it manually.

You can't hex edit the save file because then the game will say that it's corrupted, so you have to edit the values in RAM (using [Vapecord](https://github.com/RedShyGuy/Vapecord-ACNL-Plugin) for example), and then save the game. Since finding all the addresses wasn't fun, here's a list in case you need it (the save addresses are provided just because I found those first):

## Structure

```cpp
struct ACNL_Cenus_Data_Type { //Size: 0x14
  uint32_t TotalPlayerStat; //All player stats combined
  uint32_t PlayerStats[4]; //For each player
};
```

This is the structure of each census entry.
It consists of 4 stat values for each player and a hidden stat value combining all 4 player stat values.

## Offsets

"Non Player specific" stats only have a value at `TotalPlayerStat`.
"Has no total stat value" stats only have values at `PlayerStats[X]`.

| Value                              | Save offset (`garden_plus.dat`) | Note                                                |
| ---------------------------------- | ------------------------------- | --------------------------------------------------- |
| Bells earned                       | `0x72510`                       |                                                     |
| Bank account                       | `0x72524`                       |                                                     |
| Bells spent                        | `0x72538`                       |                                                     |
| Loans paid                         | `0x7254C`                       |                                                     |
| Turnips bought                     | `0x72560`                       |                                                     |
| Turnips sold                       | `0x72574`                       |                                                     |
| Turnip expenses                    | `0x72588`                       |                                                     |
| Turnip profits                     | `0x7259C`                       |                                                     |
| Public works expenses              | `0x725B0`                       |                                                     |
| Recycle Shop earnings              | `0x725C4`                       |                                                     |
| Flowers watered                    | `0x725D8`                       |                                                     |
| Fish caught                        | `0x725EC`                       |                                                     |
| Bugs caught                        | `0x72600`                       |                                                     |
| Sea creatures caught               | `0x72614`                       |                                                     |
| Public works built                 | `0x72628`                       | Non Player specific                                 |
| Fruit grown                        | `0x7263C`                       | Non Player specific                                 |
| Perfect fruit grown                | `0x72650`                       | Non Player specific                                 |
| Fruits grown on the beach          | `0x72664`                       | Non Player specific                                 |
| Flowers planted                    | `0x72678`                       |                                                     |
| Trees planted                      | `0x7268C`                       |                                                     |
| Trees cut down                     | `0x726A0`                       |                                                     |
| Dream Towns Visited                | `0x726B4`                       |                                                     |
| K.K. Slider concerts               | `0x726C8`                       |                                                     |
| Shrunk sketches                    | `0x726DC`                       |                                                     |
| Island tours                       | `0x726F0`                       |                                                     |
| Island visits                      | `0x72704`                       |                                                     |
| Letters sent                       | `0x72718`                       |                                                     |
| Furniture customized               | `0x7272C`                       |                                                     |
| Nookling’s expenses                | `0x72740`                       |                                                     |
| Gracie’s expenses                  | `0x72754`                       |                                                     |
| Gardening shop expenses            | `0x72768`                       |                                                     |
| Weeds pulled                       | `0x7277C`                       |                                                     |
| Able Sisters' expenses             | `0x72790`                       |                                                     |
| Kicks’ expenses                    | `0x727A4`                       |                                                     |
| Katrina visits                     | `0x727B8`                       |                                                     |
| StreetPass visitors                | `0x727CC`                       | Non Player specific                                 |
| Towns visited                      | `0x727E0`                       |                                                     |
| Town visitors                      | `0x727F4`                       |                                                     |
| Sahara redecorations               | `0x72808`                       |                                                     |
| Jobs at The Roost                  | `0x7281C`                       |                                                     |
| Fossils analyzed                   | `0x72830`                       |                                                     |
| Pro Designs created                | `0x72844`                       |                                                     |
| Badges obtained                    | `0x72858`                       | Has no total stat value                             |
| Helped Gulliver                    | `0x7286C`                       |                                                     |
| Shampoodle visits                  | `0x72880`                       |                                                     |
| Art pieces bought                  | `0x72894`                       |                                                     |
| Scallops given to Pascal           | `0x728A8`                       |                                                     |
| Unknown 0                          | `0x728BC`                       |                                                     |
| Balloons popped                    | `0x728D0`                       |                                                     |
| Tourney Fish caught                | `0x728E4`                       | Cleared when event ends                             |
| Tourney Insect caught              | `0x728F8`                       | Cleared when event ends                             |
| Festival Feathers caught           | `0x7290C`                       | Cleared when event ends                             |
| Eggs given to Zipper               | `0x72920`                       | Cleared when event ends                             |
| Found imposter Blanca              | `0x72934`                       | Cleared when event ends                             |
| Firework Designs given to Isabelle | `0x72948`                       | Set after fireworks start / cleared when event ends |
| Received Candy on Halloween        | `0x7295C`                       | Cleared when event ends                             |
| Harvest Festival Courses done      | `0x72970`                       | Cleared when event ends                             |
| Snowmen built by you in Town       | `0x72984`                       | Cleared when snowman melts                          |
| Given Toy Day presents             | `0x72998`                       | Cleared when event ends                             |
| Snowflakes caught                  | `0x729AC`                       | Cleared when it stops snowing                       |
| PartyPoppers popped at New Years   | `0x729C0`                       | Cleared when event ends                             |
| Total Bingo wins                   | `0x729D4`                       |                                                     |
| Shooting Star wishes               | `0x729E8`                       |                                                     |
| Unknown 1                          | `0x729FC`                       |                                                     |
| Lost items returned                | `0x72A10`                       |                                                     |
| Visited by villagers               | `0x72A24`                       |                                                     |
| Villagers visited                  | `0x72A38`                       |                                                     |
| Hide and seek matches              | `0x72A4C`                       |                                                     |
| Unknown 2                          | `0x72A60`                       |                                                     |
| Unknown 3                          | `0x72A74`                       |                                                     |
| amiibo used                        | `0x72A88`                       |                                                     |
| Reset Surveillance Center visits   | `0x72A9C`                       |                                                     |
| DJ K.K. visits                     | `0x72AB0`                       |                                                     |
| Golden Roses created               | `0x72AC4`                       | Non Player specific                                 |
| Unknown 4                          | `0x72AD8`                       | Non Player specific                                 |
| Famous Mushrooms eaten             | `0x72AEC`                       |                                                     |
| Initiatives completed              | `0x72B00`                       |                                                     |
| Coupons earned                     | `0x72B14`                       |                                                     |
| Coupons spent                      | `0x72B28`                       |                                                     |
| Unused                             | `0x72B3C`                       | Non Player specific / most likely unused            |

## Tools used

- [ImHex](https://github.com/WerWolv/ImHex)
  - To analyze the save/RAM dumps and find the values and addresses
- [NLSE](https://github.com/kwsch/NLSE)
  - To export data from my old save and import it in the new one
- [Marc Robledo's save editor](https://www.marcrobledo.com/acnl-editor/)
  - To add a few missing things after importing with NLSE
- [Citra (PabloMK7's fork)](https://github.com/PabloMK7/Citra)
  - To create the new save and test various things
- [Vapecord](https://github.com/RedShyGuy/Vapecord-ACNL-Plugin)
  - To dump and edit the RAM and find some values
- [ChatGPT](https://chatgpt.com/)
  - It was super helpful to fill in most of the missing addresses once I found the pattern

## Other stuff

- [More info on the Census Menu](https://tcrf.net/Animal_Crossing:_New_Leaf#Census_Menu)

> [!info]
> If you have something to add or fix in this table, you can contact me on [Telegram](https://t.me/LeddaZ) or [fork](https://github.com/LeddaZ/notes/fork) this website on GitHub and open a pull request.
