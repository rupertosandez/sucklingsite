---
layout: default
title: Changelog
permalink: /changelog/
---

# changelog

All notable changes to **Suckling** will be documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/),
and this project adheres to [Semantic Versioning](https://semver.org/).

## [2.3.2] - 2026-05-20

### added

- `/rent` now lets you choose how you want to rent: roll random, pick a movie yourself, or ask an admin for a recommendation.
- you can now have up to 3 active rentals at once.
- `/myrental` shows all of your active rentals when you have more than one.
- admins can use `/setrentalrequests` to choose where rental recommendation requests post.

### changed

- `/return` and `/extend` can now target a specific rental by id or title when you have multiple rentals active.
- randomly rolled rentals now have better odds for rare/iconic macguffin drops when you return them.
- watchlist buttons should be less likely to show discord's "interaction failed" message after old or expired clicks.
- movie card buttons, like **+ watchlist**, should keep working on newer public posts even after the bot restarts.

## [2.3.1] - 2026-05-20

### changed

- housekeeping update: the bot was reorganized behind the scenes so future updates are easier to ship.
- `/return` no longer needs a rating. you can return a rental with just the recommendation checkbox and optional thoughts.

## [2.3.0] - 2026-05-19

### added

- macguffins are here: collectible movie objects that can drop when members return rentals.
- `/claimguffin` gives each member one free starter macguffin.
- `/myguffins` shows your collection privately, with card details.
- `/giftguffin` lets you give one of your macguffins to another member.
- admins can use `/adminguffins` to view, add, move, remove, or randomly assign member macguffins.

## [2.2.0] - 2026-05-19

### added

- admins can use `/botstatus` for one quick dashboard with bot health, configured channels, feature toggles, rental counts, linked letterboxd count, and setup warnings.
- admins can use `/lblinked` to see which members have linked letterboxd accounts.
- letterboxd activity posting now only posts recent activity from the last 60 minutes, so old unseen watches do not flood the channel.

## [2.1.0] - 2026-05-19

### added

- linked letterboxd accounts can now feed a shared activity channel when members log new watches.
- admins can use `/setlbactivity` to choose the activity channel. the bot starts from the current feeds, so old watches will not flood the channel.
- admins can use `/lbactivitynow` to check for new letterboxd activity manually.

### changed

- `/lb tastecheck` now compares any two members or public letterboxd usernames, instead of always comparing from your own account.

## [2.0.0] - 2026-05-18

### added

- added letterboxd linking with `/lb link`, `/lb profile`, `/lb watchlist`, and `/lb group`.
- added `/lb tastecheck` to compare your recent letterboxd taste against another member or public letterboxd username.
- added personal bot watchlists with `/watchlist show`, `/watchlist add`, and `/watchlist remove`.
- movie cards now have a **+ watchlist** button so you can save films from `/suck`, `/roll`, `/rb9`, `/rb9randomscene`, and daily recommendations.
- films that are in the rb9 library now show a **rent this** button on movie cards.

### changed

- `/watchlist show` displays 10 films per page and includes a roll button for picking from your saved list.
- `/suck` and `/roll` cards now include the new watchlist/rental buttons when available.

## [1.9.0] - 2026-05-17

### added

- added a desktop launcher for running the bot from the windows tray.
- the launcher can start, stop, restart, show live logs, and update the bot with one click.
- the launcher can also be set to start with windows if you want the bot to come back automatically after a reboot.

### changed

- stopping or restarting the bot from the launcher is cleaner now, so it should shut down more gracefully.

## [1.8.0] - 2026-05-17

### added

- `/extend` lets you add 24 hours to your active rental once per rental.
- rental reminder DMs now include an **extend 24h** button.
- admins can now assign a rental to a member directly with `/assignrental`.

## [1.7.0] - 2026-05-16

### added

- admins can now restart the bot from discord with `/restart`.

## [1.6.2] - 2026-05-15

### changed

- rental buttons now show that the bot is working right away.
- rental buttons also disable after being clicked, which should prevent accidental double-click weirdness.

## [1.6.1] - 2026-05-15

### changed

- update announcements now link back to this changelog page.

## [1.6.0] - 2026-05-15

### added

- when a new bot version goes live, the bot can post an update announcement in the configured update channel.
- normal restarts will not spam the same update again.

## [1.5.1] - 2026-05-15

### changed

- the bot should feel faster and more reliable when looking up movies, checking streaming availability, pulling rb9 picks, or running daily scans.
- the first `/rb9` or `/rent` after a restart should be less sluggish.
- no command behavior changed in this update.

## [1.5.0] - 2026-05-15

### added

- added the rb9 video store rental system.
- `/rent` picks a random film from the rb9 library and gives you 48 hours to watch it.
- `/return` lets you return your rental with a rating, recommendation, and optional thoughts.
- rental reviews post to the configured discord forum.
- `/myrental` shows your current rental, due date, and review thread.
- `/latefees` shows the late fee leaderboard.
- `/rentalstats` shows rental history and stats for you or another member.
- admins can use `/setreviews` to choose the review forum.
- admins can use `/cancelrental` to cancel someone's active rental without charging a late fee.
- rb9 movie embeds can now show a rent button when the film is available in the library.
- the bot sends rental reminder DMs before a movie is due and when it goes overdue.

### notes

- you can only have one active rental at a time.
- once you have rented a movie, random `/rent` picks will not give you that same movie again.
- late fees are $1 per day overdue, calculated when you return the movie.

## [1.4.0] - 2026-05-12

### added

- `/info` shows a quick public about card for the bot, including version and uptime.

## [1.3.0] - 2026-05-12

### added

- `/play` starts trivia roulette.
- each round randomly picks a clue type like quote, emoji, tagline, or trivia.
- the first correct guess in chat wins the round.

### changed

- `/leaderboard` now includes wins from both `/guess` and `/play`.
- `/giveup` can now end `/play` rounds too.
- guessing games now avoid overlapping in the same channel.

## [1.2.4] - 2026-05-11

### changed

- `/watch` became `/suck`.
- the movie lookup behavior is the same, just with a name that fits the bot better.

## [1.2.3] - 2026-05-10

### fixed

- `/roll` is better about respecting runtime filters now.
- if it cannot find a matching movie, it will say that instead of handing you something outside the filter.

### changed

- movie lookups and availability checks should be a bit smoother behind the scenes.

## [1.2.2] - 2026-05-10

### added

- `/watch` now shows whether a movie is in the rb9 plex library.
- if the movie is not in the library, the bot can include a request link.

## [1.2.1] - 2026-05-03

### changed

- `/rb9genre` now counts each film by its main genre, making the genre breakdown cleaner.

## [1.2.0] - 2026-05-03

### added

- `/rb9stats` shows overall library stats.
- `/rb9biggest` and `/rb9shortest` show the longest and shortest movies in the library.
- `/rb9oldest` and `/rb9newest` show the oldest movie and newest library addition.
- `/rb9totalruntime` shows how long it would take to watch the whole library.
- `/rb9decade` shows films by decade.
- `/rb9genre` shows the top genres in the library.
- `/rb9randomscene` picks a random film with a backdrop image.

### changed

- `/plex` became `/rb9`.

## [1.1.1] - 2026-05-03

### changed

- `/giveup` now works for both `/guess` and `/six`.
- `/six` rounds now last 4 minutes instead of 3.

## [1.1.0] - 2026-05-03

### added

- `/six` starts a six degrees of separation game with two random actors.
- `/sixleaderboard` shows the leaderboard for that game.

### notes

- players submit actor-to-movie chains in chat.
- shorter valid chains score more points.

## [1.0.0] - 2026-05-03

### added

- first public community version of the bot.
- `/guess` now has easy and hard modes.
- `/version` shows the bot version.

### changed

- streaming announcements now only fire for first-time digital releases.
- movies moving between services should no longer create extra announcement noise.

## [0.9.0] - pre-release

### added

- added `/plex`, the first version of the random rb9 library picker.
- streaming announcements became smarter about only announcing new availability.

## [0.8.0] - pre-release

### added

- admins can use `/toggle` to turn streaming announcements and daily recommendations on or off.

## [0.7.0] - pre-release

### added

- `/guess` gained movie stills as another guessing mode.
- `/guess` can now randomize between poster and still rounds.

## [0.6.0] - pre-release

### added

- added the original `/guess` movie poster game.
- added `/giveup`.
- added `/leaderboard`.

## [0.5.0] - pre-release

### added

- `/roll` picks a random horror movie, with optional decade and runtime filters.
- daily horror recommendations can post automatically at noon.
- admins can use `/setdaily` and `/dailynow` to manage daily recommendations.

## [0.4.0] - pre-release

### added

- `/track`, `/untrack`, and `/tracked` let the community manage a watchlist.
- admins can choose the streaming alert channel.
- admins can manually run streaming checks.
- the bot can automatically check each morning for newly available movies.

## [0.3.0] - pre-release

### added

- added saved bot data so tracked movies and settings can stick around after restarts.

## [0.2.0] - pre-release

### added

- `/watch` shows where a movie is available to watch.
- ambiguous movie searches now offer a dropdown so you can pick the right title.
- `/watch` supports a year option for more specific searches.

## [0.1.0] - pre-release

### added

- added the first `/ping` health check.
- added the first `/watch` movie lookup command.
