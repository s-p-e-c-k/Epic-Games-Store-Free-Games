# Epic Free Games — Auto‑Updated Weekly

This repository automatically fetches the current free games available on the Epic Games Store and updates the list every Thursday (the day Epic refreshes its weekly free titles). The results are written into **FREE_GAMES.md**, along with a JSON dump for anyone who wants to use the data programmatically.

---

## What this repo does

- Checks the Epic Games Store API once per week  
- Detects all games currently marked as **free**  
- Writes the titles into `FREE_GAMES.md`  
- Saves the raw API results in `free_games.json`  
- Automatically commits the update to the repo  

Everything is handled through GitHub Actions — no manual work required.

---

## How it works

The workflow uses Epic’s public promotions API:

https://store-site-backend-static.ak.epicgames.com/freeGamesPromotions


It filters entries where:

- `discountPrice = 0`  
- or the game is tagged under `freegames`

These fields come directly from Epic’s catalog data.

The workflow runs every Thursday using a cron schedule and can also be triggered manually through the **Run workflow** button in GitHub Actions.
