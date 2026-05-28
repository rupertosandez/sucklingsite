---
layout: default
title: Commands
permalink: /commands/
---

# commands

a reference for everything **Suckling** can do. all commands are slash commands, type `/` in any channel where the bot has access to see them in autocomplete.

suckling is built for the **Return by 9** movie community~

---

## about the bot

### `/info`
quick about card for the bot.

---

## lookup & discovery

### `/suck <title> [year]`
look up a movie. returns a card with the synopsis, director, runtime, where to watch it (theaters, streaming), and whether or not it's available in the RB9 plex library. cards include **+ watchlist**, and show **rent this** when the film is in rb9.

- `title` (required): the movie title to search for
- `year` (optional): filter by release year if multiple matches exist

if multiple films share a title (e.g. "halloween"), a dropdown will appear so you can pick the right one. you can also pre-filter with `year` to skip the dropdown.

examples:
- `/suck The Substance`
- `/suck Halloween year:1978`

---

### `/roll [decade] [runtime]`
get a random movie recommendation. filters are optional — leave blank for a fully random pick. cards include **+ watchlist**, and show **rent this** when the film is in rb9.

- `decade` (optional): e.g. `1980s`, `2010s`
- `runtime` (optional): `short` (under 90 min), `medium` (90-120 min), or `long` (over 120 min)

examples:
- `/roll`
- `/roll decade:1980s`
- `/roll decade:2020s runtime:short`

---

## return by 9 library

commands that pull from the return by 9 plex library.

### `/rb9`
picks a random movie from the library. returns title, summary, runtime, and poster. includes **+ watchlist** and **rent this**.

### `/rb9stats`
overall library summary: total movie count, total runtime, year range, oldest film, newest film, most recently added, average rating.

### `/rb9biggest`
the longest film in the library by runtime.

### `/rb9shortest`
the shortest film in the library by runtime (excludes very short entries under 30 minutes).

### `/rb9oldest`
the oldest film in the library by release year.

### `/rb9newest`
the most recently added film in the library.

### `/rb9totalruntime`
fun stats on how long it'd take to watch the entire library back-to-back, including a "8 hours per day" estimate.

### `/rb9decade`
bar chart breakdown of films per decade in the library.

### `/rb9genre`
top 10 genres in the library by count.

### `/rb9randomscene`
a random film + a random backdrop image from it. includes **+ watchlist** and **rent this**.

---

## video store

rent a film from the RB9 library. the clock starts when you confirm — it's due by 9 pm on the fifth day, and you use `/return` to post your review.

### `/rent`
start a rental from the library. you can have up to **3 active rentals** at once.

if you've set `/timezone`, rentals are due at 9 pm in your timezone. otherwise the bot uses the server default timezone.

the rental menu has three paths:

- **roll random** - get a random film, with up to **2 re-rolls** before the bot locks one in
- **pick a movie** - choose a specific rb9 title yourself
- **ask an admin** - post a recommendation request so an admin can assign a pick

random rolls work like this:

1. bot shows a film: **[ accept rental ]** **[ re-roll ]**
2. first reroll: bot shows another film: **[ accept rental ]** **[ re-roll (last one) ]**
3. second reroll (final): bot picks a third film and locks it in automatically — no choice

films you've rented before are never offered again (all-time exclusion, any status).

randomly rolled rentals have better odds for rare/iconic macguffin drops when returned.

> you can also rent a specific film directly from the **rent this** button on `/rb9`, `/rb9randomscene`, `/suck`, `/roll`, and the daily recommendation — no rerolls for those since you're choosing intentionally.

---

### `/timezone [timezone_name] [clear]`
set your rental timezone so due dates land at 9 pm where you are.

- `timezone_name` (optional): timezone like `America/Los_Angeles`, `America/New_York`, or `Europe/London`
- `clear` (optional): clear your saved timezone and use the server default

run it with no options to check your current rental timezone.

---

### `/return <recommend> [rating] [thoughts] [rental]`
return a rental, post a review to the forum, and roll for a macguffin drop.

- `recommend` (required): checkbox — would you recommend this to the group?
- `rating` (optional): your score out of 10 (1-10)
- `thoughts` (optional): your review, as brief or long as you like
- `rental` (optional): rental id or part of the title, needed if you have more than one active rental

on return, the forum thread is edited in-place: updated with your rating if you gave one and your review, renamed from "checked out" to "reviewed", and the **recommendation** forum tag is added if you checked yes.

if you return it late, a late fee is calculated: **$1 for every day (or part of a day) overdue**. fees are cosmetic — tracked in the ledger but not collected.

---

### `/myrental`
shows your active rentals, due times, and rental ids. if you only have one active rental, it shows the full rental status with the forum thread.

ephemeral — only you see it.

---

### `/extend [rental]`
extend an active rental by 24 hours. each rental can be extended once.

- `rental` (optional): rental id or part of the title, needed if you have more than one active rental

the 12-hour reminder DM also includes an **extend 24h** button.

---

### `/setrentalrequests <channel>`
admin only. choose where **ask an admin** rental recommendation requests post.

- `channel` (required): the text channel for admin recommendation pings

---

### `/latefees`
leaderboard of accumulated late fees. shows total fees, total rentals, and late return count per person.

---

### `/rentalstats [user]`
your full rental history and stats: total rentals, on-time vs late, total fees, currently renting (if applicable), and your last 5 returns with ratings.

- `user` (optional): check another member's stats

---

## macguffins

macguffins are collectible movie objects. every one is unique, so once someone claims a card, nobody else can pull that same one.

returning a rental can drop a macguffin publicly in the channel.

### `/claimguffin`
claim your one free starter macguffin.

### `/myguffins`
view your macguffin collection privately. shows 5 at a time, with a button to open each card.

### `/giftguffin @user <card>`
gift one of your macguffins to another member. partial names work if the bot can tell which card you mean.

---

## achievements

earn movie-club badges by using suckling. anything about watching movies comes from returned rentals, so `/return` is the official record.

you can earn as many achievements as you want, but only **3** can be pinned as visible discord badge roles at once.

### `/achievements [user]`
view an achievement shelf.

- leave `user` blank to see your own private shelf, visible badges, recent unlocks, and progress hints
- choose another member to see their public shelf

### `/achievementdisplay <achievement> [replace]`
pin an earned achievement as one of your visible badge roles.

- `achievement` is one of your unlocked badges
- `replace` lets you swap out a visible badge when your 3 slots are full

### `/achievementhide <achievement>`
hide one visible badge role. the achievement stays unlocked.

### `/achievementclear`
remove all visible achievement badge roles.

### `/achievementboard`
community achievement board with newest unlocks, top shelves, and rare badges.

---

## tracking

### `/track <title> [year]`
add a movie to the watchlist. the bot will announce it in the streaming-alerts channel when it becomes available digitally for the first time. if the film is *already* streaming, the bot will tell you immediately and link to where.

- `title` (required): the movie title to track
- `year` (optional): filter by year if there are multiple matches

example: `/track The Conjuring Last Rites`

---

### `/untrack <title>`
remove a movie from the watchlist.

- `title` (required): the title or part of the title to remove

example: `/untrack conjuring`

---

### `/tracked`
show every movie currently being tracked, plus who added each one.

---

## letterboxd

link your letterboxd account, browse watchlists, and compare recent taste.

### `/lb link <username>`
connects your letterboxd account. the account needs to be public.

### `/lb unlink`
removes your linked letterboxd account.

### `/lb profile [user] [username]`
shows recent diary entries: films watched, ratings, dates, and review snippets.

- `user` (optional): a server member who linked letterboxd
- `username` (optional): a raw letterboxd username
- leave both blank to see your own profile

### `/lb watchlist [user] [username]`
browse a letterboxd watchlist. includes:

- **roll from this** - picks a random film from that watchlist
- **import all** - adds the watchlist to your personal bot watchlist

### `/lb group`
shows recent diary activity from linked members, grouped by member so it's easier to skim.

linked accounts may also appear in the server's letterboxd activity channel if admins have enabled it.

### `/lb tastecheck [a_user] [b_user] [a_username] [b_username]`
compares two letterboxd accounts and gives a recent taste compatibility readout.

- use discord members if they've linked accounts with `/lb link`
- use raw usernames to compare anyone with public letterboxd accounts
- pick one target for side a and one target for side b

---

## personal watchlist

a private film queue that lives in the bot.

### `/watchlist show`
shows your watchlist, 10 films per page. includes a remove dropdown and a roll button.

### `/watchlist add <title> [year]`
adds a film by title. if there are multiple matches, the bot asks you to pick the right one.

### `/watchlist remove <title>`
removes films from your list by partial title match.

you can also add films with the **+ watchlist** button on movie cards.

---

## games

### `/play`
start a trivia roulette round. the bot randomly picks one of four categories and posts a clue. first person to guess correctly in chat wins.

categories:
- 🎬 **quote** - a memorable line of dialogue
- 🎭 **emoji** - the film described in emoji
- 📜 **tagline** - the marketing tagline from posters or trailers
- 🎞️ **trivia** - a piece of behind-the-scenes or production trivia

30-second time limit per round. 1 point per win. shares the leaderboard with `/guess` (use `/leaderboard` to see standings).

only one round can be active in a channel at a time. `/giveup` ends the round.

example: `/play`

### `/guess [difficulty]`
start a guessing round. the bot posts an image and the first person to guess correctly in chat wins. 60-second time limit per round.

- `difficulty` (optional): `easy` (full movie still, 1 point) or `hard` (cropped poster, 2 points). default: random.

only one round can be active in a channel at a time.

examples:
- `/guess`
- `/guess difficulty:easy`
- `/guess difficulty:hard`

---

### `/six`
start a six degrees of separation round. the bot picks two random popular actors and challenges players to connect them through shared films.

submit chains in chat using this format:
```
Actor -> Film -> Actor -> Film -> Actor
```

first valid chain wins. shorter chains earn more points:

| films in chain | points |
| -------------- | ------ |
| 1              | 5      |
| 2              | 4      |
| 3              | 3      |
| 4              | 2      |
| 5+             | 1      |

maximum chain length is 6 films. round duration is 4 minutes.

---

### `/giveup`
end the current round (works for both `/guess` and `/six`). anyone in the channel can call it.

---

### `/leaderboard`
show the top scorers for `/guess`.

### `/sixleaderboard`
show the top scorers for `/six`.

---

## auto-posting features

the bot automatically posts in a few ways (admins configure the channels):

🩸 **daily recommendation** - every day at noon, the bot drops a random pick in the configured channel.

📺 **streaming announcements** - when a movie becomes available digitally for the first time (shudder, netflix, max, etc.), the bot announces it in the configured channel. shudder additions get a special highlight.

**letterboxd activity** - linked members' new diary entries can post to a shared activity channel.

**suckling feed** - achievement unlocks can post to a shared feed channel.

the streaming feature only announces films hitting digital for the first time — not when they move between services or get added to additional ones.

---

## quick tips

- movie titles in `/suck` and `/track` support fuzzy matching, so you don't need exact punctuation or capitalization
- the dropdown menu that appears for ambiguous titles times out after 60 seconds — just run the command again if it expires
- film cards can be saved with **+ watchlist**; rb9 films can also be rented with **rent this**
- your personal `/watchlist show` command is private
- both games and tracking are server-wide — anyone can add to the tracked list and play
- leaderboards are separate for `/guess` and `/six` — winning at one doesn't affect the other

---

# admin commands

> these commands require the **manage server** permission and are hidden from regular members.

### `/botstatus`
admin dashboard for the bot: version, uptime, latency, cache size, configured channels, auto-posting toggles, tracked film count, linked letterboxd count, active rentals, overdue rentals, and setup warnings.

### `/lblinked [page]`
list linked letterboxd accounts. shows each discord member, their letterboxd profile, and when they linked it. use `page` if the list is long.

### `/setreviews <forum_channel>`
set the forum channel where rental reviews post. the bot needs create public threads and send messages in threads permissions. auto-detects rental and recommendation forum tags if they exist.

### `/cancelrental @user [reason]`
cancel a member's active rental with no late fee. edits the forum thread and DMs the member. optionally include a reason.

### `/assignrental @user <title> [year]`
assign an rb9 library rental to a member. creates the rental, opens the review thread, and DMs them the due date.

### `/adminguffins <action> @user [card]`
view or edit a member's macguffins.

- `view`: shows the member's current collection
- `add`: adds a macguffin by name or id; if someone else has it, moves it
- `remove`: removes a macguffin from that member's collection
- `random`: assigns the member a random unclaimed macguffin

### `/setannouncements <channel>`
set the channel where streaming announcements post. the bot needs send-message and embed-link permissions in the chosen channel.

### `/setdaily <channel>`
set the channel where the daily recommendation posts (at noon).

### `/setlbactivity <channel>`
set the channel where new watches from linked letterboxd accounts post. when this is set, the bot starts from the current feeds so older watches do not flood the channel.

### `/setfeed <channel>`
set the channel where suckling feed posts go, including achievement unlocks.

### `/toggle <feature> <enabled>`
enable or disable an auto-posting feature without removing the channel setting.

- `feature`: `streaming announcements`, `daily recommendation`, or `letterboxd activity`
- `enabled`: `True` or `False`

### `/checknow`
manually trigger the streaming check in dry-run mode. doesn't post to discord — just returns a summary of what *would* be announced. useful for verifying detection.

### `/restart`
restart the bot process. useful after pulling updates or clearing a stuck runtime state.

### `/checknowlive`
manually trigger the streaming check **and post** announcements live. use sparingly.

### `/dailynow`
manually trigger today's daily recommendation post.

### `/lbactivitynow [post]`
manually check linked letterboxd activity. by default it reports what it found and how much is recent enough to post; set `post:True` to post entries from the last 60 minutes only.

### `/plexcleanupnow [post]`
admin only. run the plex cleanup check manually. by default it only shows a private summary; set `post:True` to post cleanup candidates to the announcement channel.

### `/plexunpopular`
admin only. show low-watch rb9 titles with lower tmdb scores, useful when reviewing what should stay in the library.

### `/achievementrescan [user]`
backfill achievements from existing suckling history. leave `user` blank to rescan everyone.

### `/achievementsyncroles <user>`
reapply a member's selected visible achievement badge roles. useful if roles were manually changed in discord.

### `/cachestats [clear]`
show the size of the in-memory cache. pass `clear:True` to wipe both the tmdb cache and the random-pick pool (useful if data feels stale).

### `/version`
show the bot's current version.

### `/ping`
quick health check — replies with the bot's latency. available to everyone, but mostly used for debugging.
