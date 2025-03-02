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

## Addresses

| Value                     | RAM addresses              | Save addresses (`garden_plus.dat`) |
| ------------------------- | -------------------------- | ---------------------------------- |
| Bells earned              | `0x31F57C10`, `0x31F57C14` | `0x72510`, `0x72514`               |
| Bank account              | `0x31F57C24`, `0x31F57C28` | `0x72524`, `0x72528`               |
| Bells spent               | `0x31F57C38`, `0x31F57C3C` | `0x72538`, `0x7253C`               |
| Loans paid                | `0x31F57C4C`, `0x31F57C50` | `0x7254C`, `0x72550`               |
| Turnips bought            | `0x31F57C60`, `0x31F57C64` | `0x72560`, `0x72564`               |
| Turnips sold              | `0x31F57C74`, `0x31F57C78` | `0x72574`, `0x72578`               |
| Turnip expenses           | `0x31F57C88`, `0x31F57C8C` | `0x72588`, `0x7258C`               |
| Turnip profits            | `0x31F57C9C`, `0x31F57CA0` | `0x7259C`, `0x725A0`               |
| Public works expenses     | `0x31F57CB0`, `0x31F57CB4` | `0x725B0`, `0x725B4`               |
| Recycle Shop earnings     | `0x31F57CC4`, `0x31F57CC8` | `0x725C4`, `0x725C8`               |
| Flowers watered           | `0x31F57CD8`, `0x31F57CDC` | `0x725D8`, `0x725DC`               |
| Fish caught               | `0x31F57CEC`, `0x31F57CF0` | `0x725EC`, `0x725F0`               |
| Bugs caught               | `0x31F57D00`, `0x31F57D04` | `0x72600`, `0x72604`               |
| Sea creatures caught      | `0x31F57D14`, `0x31F57D18` | `0x72614`, `0x72618`               |
| Public works built        | `0x31F57D28`               | `0x72628`                          |
| Fruit grown               | `0x31F57D3C`               | `0x7263C`                          |
| Perfect fruits grown      | `0x31F57D50`               | `0x72650`                          |
| Fruits grown on the beach | `0x31F57D64`               | `0x72664`                          |
| Flowers planted           | `0x31F57D78`, `0x31F57D7C` | `0x72678`, `0x7267C`               |
| Trees planted             | `0x31F57D8C`, `0x31F57D90` | `0x7268C`, `0x72690`               |
| Trees cut down            | `0x31F57DA0`, `0x31F57DA4` | `0x726A0`, `0x726A4`               |
| K.K. Slider concerts      | `0x31F57DC8`, `0x31F57DCC` | `0x726C8`, `0x726CC`               |
| Shrunk sketches           | `0x31F57DDC`, `0x31F57DE0` | `0x726DC`, `0x726E0`               |
| Badges obtained           | `0x31F57DF0`, `0x31F57DF4` | `0x726F0`, `0x726F4`               |
| Art pieces bought         | `0x31F57E04`, `0x31F57E08` | `0x72704`, `0x72708`               |
| Letters sent              | `0x31F57E18`, `0x31F57E1C` | `0x72718`, `0x7271C`               |
| Furniture customized      | `0x31F57E2C`, `0x31F57E30` | `0x7272C`, `0x72730`               |
| Nookling’s expenses       | `0x31F57E40`, `0x31F57E44` | `0x72740`, `0x72744`               |
| Gracie’s expenses         | `0x31F57E54`, `0x31F57E58` | `0x72754`, `0x72758`               |
| Gardening shop expenses   | `0x31F57E68`, `0x31F57E6C` | `0x72768`, `0x7276C`               |
| Weeds pulled              | `0x31F57E7C`, `0x31F57E80` | `0x7277C`, `0x72780`               |
| StreetPass visitors       | `0x31F57ECC`, `0x31F57ED0` | Unknown                            |
| Towns visited             | `0x31F57EE0`, `0x31F57EE4` | `0x727E0`, `0x727E4`               |
| amiibo used               | `0x31F57F08`, `0x31F57F0C` | `0x72808`, `0x7280C`               |
| Jobs at The Roost         | `0x31F57F1C`, `0x31F57F20` | `0x7281C`, `0x72820`               |
| Fossils analyzed          | `0x31F57F30`, `0x31F57F34` | `0x72830`, `0x72834`               |
| Island tours              | `0x31F57F5C`               | `0x7285C`                          |
| Helped Gulliver           | `0x31F57F6C`, `0x31F57F70` | `0x7286C`, `0x72870`               |
| Shampoodle visits         | `0x31F57F80`, `0x31F57F84` | `0x72880`, `0x72884`               |
| Island visits             | `0x31F57F94`, `0x31F57F98` | `0x72894`, `0x72898`               |
| Scallops given to Pascal  | `0x31F57FA8`, `0x31F57FAC` | `0x728A8`, `0x728AC`               |
| Balloons popped           | `0x31F57FD0`, `0x31F57FD4` | `0x728D0`, `0x728D4`               |
| Unknown                   | `0x31F580AC`, `0x31F580B0` | `0x729AC`, `0x729B0`               |
| Sahara redecorations      | `0x31F58100`, `0x31F58104` | `0x72A00`, `0x72A04`               |
| Lost items returned       | `0x31F58110`, `0x31F58114` | `0x72A10`, `0x72A14`               |
| Villagers visited         | `0x31F58124`, `0x31F58128` | `0x72A24`, `0x72A28`               |
| Visited by villagers      | `0x31F58138`, `0x31F5813C` | `0x72A38`, `0x72A3C`               |
| Hide and seek matches     | `0x31F5814C`, `0x31F58150` | `0x72A4C`, `0x72A50`               |
| Unknown                   | `0x31F58174`, `0x31F58178` | `0x72A74`, `0x72A78`               |
| Unknown                   | `0x31F58188`, `0x31F5818C` | `0x72A88`, `0x72A8C`               |
| DJ K.K. visits            | `0x31F581B0`, `0x31F581B4` | `0x72AB0`, `0x72AB4`               |
| Initiatives completed     | `0x31F58200`, `0x31F58204` | `0x72B00`, `0x72B04`               |
| Coupons earned            | `0x31F58214`, `0x31F58218` | `0x72B14`, `0x72B18`               |
| Coupons spent             | `0x31F58228`, `0x31F5822C` | `0x72B28`, `0x72B2C`               |
| Able Sisters' expenses    | `0x31F71390`, `0x31F71394` | `0x72790`, `0x72794`               |
| Kicks’ expenses           | `0x31F713A4`, `0x31F713A8` | `0x727A4`, `0x727A8`               |
| Katrina visits            | `0x31F713B8`, `0x31F713BC` | `0x727B8`, `0x727BC`               |

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
