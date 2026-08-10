---
layout: default
title: Changelog
permalink: /changelog/
---

# Changelog

All notable changes to **Suckling** will be documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/),
and this project adheres to [Semantic Versioning](https://semver.org/).

## [2.29.1] - 2026-08-09

### Changed

- Words are now called stickers. `/mywords` is now `/mystickers`.

## [2.29.0] - 2026-08-09

### Added

- Returning a tape can drop a sticker. Stickers are a new collectible:
  you find them by using the site, and combine up to three into a title
  on your profile.
- `/mystickers` lists the stickers you have found.

## [2.28.0] - 2026-08-09

### Added

- Watched return reviews can be edited from the website.
- Journal entries you wrote can be deleted from the website.

### Changed

- The recommendation on a return is optional.
- Recommendations display as a thumbs up or down.

### Fixed

- A return with no opinion no longer shows as not recommended.

## [2.27.4] - 2026-08-04

### Changed

- Renamed four taste axes for clarity: "old" is now "older", "long" is
  "longer", "roaming" is "genre range", "world" is "non-English".

## [2.27.3] - 2026-08-03

### Fixed

- A Letterboxd watch with no review written no longer posts one. The
  activity feed showed the watch date as if it were the review.

## [2.27.2] - 2026-08-03

### Fixed

- Letterboxd reviews written with formatting arrive as plain text. A review
  using a blockquote or bold text used to show its markup. A review that
  links out keeps the address alongside the text.

## [2.27.1] - 2026-08-03

### Changed

- The wait before a rental can be returned as watched is the film's own
  runtime, not a flat 24 hours. Returning it unwatched is unchanged and
  available at any time.

## [2.27.0] - 2026-08-03

### Changed

- A rental can be returned as watched 24 hours after it was rented.
  Returning it unwatched is unchanged and available at any time.

## [2.26.2] - 2026-08-03

### Fixed

- Rentals started from the website are filed under your name. A member
  who signed up with Google had no Discord account for the bot to read a
  name from, so their rentals were labelled "member" and a number, which
  is how they showed up on film pages.

## [2.26.1] - 2026-08-03

### Fixed

- Anything you do in Discord is now filed against your account rather
  than your Discord login. These are the same thing for almost everyone,
  and different for a member who made their account on the website with
  Google and connected Discord afterwards - for them a rental started in
  Discord would not have shown up on the website at all.

## [2.26.0] - 2026-08-02

### Changed

- Dates on the website now read in your own timezone. They were shown in UTC, which put them a day ahead in the evening for anyone west of it.
- The website works out your timezone from your browser and remembers it, so rentals come due at 9 pm where you are without setting anything. A timezone you chose yourself is never overwritten.
- Your timezone can be set on the website, under Settings -> Privacy and sync. It was Discord-only before.
- `/timezone` still works and saves through the website. If the site does not answer, it says so instead of reporting success.

### Fixed

- A timezone set with `/timezone` could be saved somewhere nothing reads it, for members who sign in with Google and linked Discord afterwards. Their rentals came due at 9 pm club time instead.

## [2.25.1] - 2026-08-02

### Changed

- Taste chips are more specific. At most one decade and two genres, so the keywords that actually distinguish you get the space.
- TMDB bookkeeping keywords no longer appear as chips: credits tags, source tags like "based on novel or book", and a set of mood adjectives. Words that describe a film's register are kept.

## [2.25.0] - 2026-08-02

### Added

- Taste profiles. A shape built from what you rent, log, rate and recommend, updating on its own as you watch. Six axes place you against the club: deep cuts, old, long, roaming, contrarian, world.
- A taste tab on your profile, with a chart, the facets that make you most distinctive, and who you are closest to. Viewing another member overlays your shape on theirs.
- `/taste` in Discord shows the same profile, and `/taste @member` compares two.
- Taste needs 10 rated or logged films before it appears. It is not a score and it is not a ranking.

## [2.24.0] - 2026-08-02

### Changed

- Any film can be rented, whatever you would watch it on. The rent button appears on every film card and film page.
- Admin rental assignment accepts any film, respects the three-rental limit, and refuses suspended accounts.

### Removed

- The request button on film pages. There is nothing to request now that any film can be rented.

## [2.23.0.1] - 2026-08-02

### Removed

- Retired an internal worker that copied shelves to a service no longer in use.

## [2.23.0] - 2026-08-01

### Added

- Explore: the portal's shelves, browsed one at a time. Replaces the Films page; Curation lives on its Community tab.
- Brent can pick from a shelf. A new door at the counter, and a matching line on every shelf.

### Changed

- Shelf rolls use the standard MacGuffin odds.

## [2.22.0] - 2026-07-30

### Added

- New members get a welcome message when they join the server.

### Changed

- Picking a title by name in `/rent` searches the whole catalog, not only the films the club hosts.

## [2.21.1] - 2026-07-30

### Changed

- Rental confirmation messages use proper sentence case.
- The counter's offer shows the film description, director and first-billed cast.
- A Tight 90 runtime filter, for films within five minutes of 90.

## [2.21.0] - 2026-07-30

### Changed

- Rolls draw from the streaming services you set on the portal.
- The portal roll page became the counter: ask Brent to pick, or narrow it down by decade, runtime and genre.

## [2.20.0] - 2026-07-29

### Added

- A setting for whether previously rented films appear in rolls. On by default.

## [2.19.6] - 2026-07-29

### Added

- Rentals no longer require a title to be on Plex.

## [2.19.5] - 2026-07-29

### Added

- Groundwork for renting titles that aren't on Plex.

## [2.19.4.2] - 2026-07-29

### Fixed

- Fixed a false alarm in internal logging.

## [2.19.4.1] - 2026-07-28

### Added

- Added an internal connection between the bot and the site.

## [2.19.4] - 2026-07-28

### Fixed

- Added double-click protection to the rental flow.

## [2.19.3] - 2026-07-28

### Added

- Safeguards so the bot refuses to start against the wrong database, and
  two copies can never run at once.

## [2.19.2.2] - 2026-07-28

### Fixed

- Bot status on the admin dashboard reported the bot as down while it was
  running normally.

## [2.19.2.1] - 2026-07-28

### Changed

- Behind-the-scenes work on where the bot runs. Nothing changes for members.

## [2.19.2] - 2026-07-27

### Fixed

- Rolling for a rental on the portal survives leaving the page. Your rolls
  are saved, "Rent a Film" takes you back to the offer you were on, and an
  offer stays takeable for a full day instead of half an hour.

## [2.19.1] - 2026-07-23

### Fixed

- Guest book DMs now link through returnby9.com and no longer show a
  Discord-branded preview card.

## [2.19.0] - 2026-07-23

### Added

- Guest book DMs: when someone signs your guest book on the portal, the bot
  sends you a short Discord DM with a link to your guest book. You can turn
  these off in the portal under Settings > Account.

## [2.18.2] - 2026-07-23

### Changed

- Renamed 23 badges across the catalog so every badge name works as a member
  display title. Progress, unlocks, and badge roles are unaffected; only the
  names changed.

## [2.18.1] - 2026-07-23

### Fixed

- Replaced the flag emoji on two badges with emoji that display correctly on
  Windows.

## [2.18.0] - 2026-07-22

### Added

- 25 new achievement badges across rentals, directors, actors, franchises,
  genres, games, and MacGuffin gifting.

### Changed

- Renamed some badges so they work better as display titles. Progress and
  unlocks are unaffected; only the names changed.

## [2.17.0] - 2026-07-19

### Added

- A new batch of MacGuffins in the drop pool.
- Five new MacGuffin sets, each with its own achievement.

## [2.16.0] - 2026-07-19

### Added

- The bot now reports its status to the portal once a minute, so admins can
  see that it is running and are notified quickly if it is not.

## [2.15.0] - 2026-07-16

### Changed

- New MacGuffins can now be added to the drop pool at any time.

## [2.14.1] - 2026-07-16

### Fixed

- Member avatars on the portal now stay up to date automatically, including
  for members who never sign in to the portal.

## [2.14.0] - 2026-07-16

### Added

- Member collections: members can build collections of films on the portal,
  show them on their profile, and submit them for review. Approved collections
  are added to Plex and appear on the Curation page credited to the member.

## [2.13.1] - 2026-07-16

### Fixed

- The "request it" link on films not in the library points to the correct
  destination again.

## [2.13.0] - 2026-07-15

### Added

- Watchlists on the portal: films can be added or removed from any film page,
  managed from the member profile, and are flagged in watch together rooms.
- Film pages for films outside the library: searching films not in the
  library creates a full film page, including the journal and watchlist
  support.

## [2.12.1.1] - 2026-07-14

### Fixed

- Portal rental requests are now picked up near-instantly instead of within a
  few seconds.

## [2.12.1] - 2026-07-14

### Fixed

- When rerolls run out on a portal rental roll, the member now picks their
  preferred film from the three shown, matching the Discord behavior.
- Poster and button layout cleanup on the new portal pages.

## [2.12.0] - 2026-07-14

### Added

- Returns and random rolls on the portal: rentals can be returned with a
  review from the member profile, and random rentals can be rolled at
  /rentals/roll with two rerolls and the same MacGuffin odds as Discord.

## [2.11.0] - 2026-07-14

### Added

- Renting from the portal: the rent button on any film page starts a rental
  with the same Discord thread, due dates, and MacGuffin odds as renting in
  Discord. Random rolls remained Discord-only in this release.

## [2.10.4.1] - 2026-07-14

### Added

- Backend groundwork for accepting rental requests from the portal. No
  member-facing changes.

## [2.10.4] - 2026-07-14

### Changed

- MacGuffin drops on returns are no longer guaranteed. Each watched return
  now has a 50% chance to drop one. Random rolls keep improved rarity odds
  when a drop occurs.

## [2.10.3.3] - 2026-07-14

### Fixed

- Collection posters now display on the portal's Curation page.

## [2.10.3.2] - 2026-07-13

### Changed

- Plex collections are now synced to the portal, powering the Curation
  section.

## [2.10.3.1] - 2026-07-11

### Changed

- Internal maintenance to improve future update deployment. No member-facing
  changes.

## [2.10.3] - 2026-07-10

### Fixed

- Improved command response times across the board, especially `/suck`,
  `/rent`, and `/return`.

## [2.10.2] - 2026-07-10

### Fixed

- Wins in `/play` and `/six` are now announced immediately instead of waiting
  on the background achievement check.

## [2.10.1] - 2026-07-10

### Fixed

- `/achievementboard` no longer errors.
- `/achievements` layout cleanup: a progress bar at the top, less clutter,
  and a link to the member's full badge page on the site.

## [2.10.0] - 2026-07-09

### Added

- `/guffinhistory <card>` shows a MacGuffin's ownership history.
- Weekly community recap: every Sunday, a summary posts to the feed channel
  with top renters, new MacGuffin pulls, achievement unlocks, and current
  game leaders.

### Changed

- `/myrental` now shows full detail for every active rental.
- `/achievements` now separates pinned badges, other earned badges, and
  upcoming badges more clearly.

## [2.9.1.2] - 2026-07-09

### Changed

- Internal maintenance. No member-facing changes.

## [2.9.1.1] - 2026-07-01

### Changed

- Movie search now handles capitalization consistently.
- Internal cleanup.

## [2.9.1] - 2026-07-01

### Changed

- General internal cleanup and optimization.

## [2.9.0] - 2026-06-18

### Added

- `/track` now sends an alert when a tracked movie becomes available to rent
  or buy on a digital store (Apple TV, Google Play, Amazon Video, etc.), in
  addition to subscription streaming alerts. Rent/buy and subscription
  availability are announced separately, so the dedicated subscription alert
  (including the Shudder alert) still fires when the movie later starts
  streaming.

### Changed

- The `/track` confirmation now notes whether a movie is already available to
  rent or buy, in addition to whether it is already streaming.

## [2.8.0] - 2026-06-16

### Added

- `/rent`: after both rerolls are used, the member now picks their preferred
  film from all films shown, instead of the last one being locked in. A
  dropdown switches the preview and an accept button confirms the pick.

## [2.7.7] - 2026-06-16

### Changed

- All remaining commands now run database work off the main loop, so
  individual commands no longer make the bot unresponsive.
- Update announcements are now written in plain language instead of
  repeating the developer changelog.

## [2.7.6] - 2026-06-16

### Changed

- Database access is more efficient, so the bot stays responsive and no
  longer misses scheduled posts under load.

## [2.7.5] - 2026-06-16

### Fixed

- Achievement rescans no longer make the bot unresponsive or block other bot
  activity while badges are checked.

## [2.7.4] - 2026-06-10

### Fixed

- `/guess` now reveals the answer immediately when someone guesses
  correctly, even if score or achievement updates are slow.

## [2.7.3] - 2026-06-10

### Fixed

- Game rounds now reveal the answer normally when someone guesses correctly,
  even if score or achievement updates need a retry.

## [2.7.2] - 2026-06-09

### Fixed

- Game wins are recorded correctly again for `/guess`, `/play`, and `/six`.

## [2.7.1] - 2026-06-07

### Changed

- The web dashboard now stays synced with bot activity as members earn
  achievements, collect MacGuffins, use rentals, and update watchlists.

## [2.7.0] - 2026-06-06

### Added

- 42 new MacGuffins.
- MacGuffin sets: completing a set unlocks a set achievement.
- MacGuffin cards now show which set an item belongs to.
- Update posts now include the latest changelog notes.

## [2.6.1] - 2026-06-05

### Fixed

- Rental threads now receive the review forum tag when a rental is returned
  with written thoughts.
- `/setreviews` now looks for the forum's review tag along with the rental
  and recommendation tags.

## [2.6.0] - 2026-06-05

### Added

- `/plexrefresh` lets admins refresh the library snapshot when RB9 has a new
  or changed title the bot does not see yet.

### Fixed

- RB9 title matching now treats `&` and `and` as equivalent, so titles like
  **Peter & The Wolf** show as rentable when they are in the library.

## [2.5.9] - 2026-06-01

### Changed

- Embeds across the bot are cleaner and more consistent: titles, field
  labels, and footers are formatted consistently throughout.
- Rental return modal labels and the return flow were cleaned up.
- The recommend field on rental reviews now shows 👍 or 👎 instead of
  "yes" / "no".
- Rental status only shows the overdue notice when the rental is overdue.
- Achievement unlock posts have less repetition.
- The achievement board's "top shelves" section is now called "top
  collectors".
- Removed redundant information from several embeds: `/rb9stats` no longer
  duplicates oldest/newest, `/rb9totalruntime` drops the raw minute count,
  and the MacGuffin card no longer repeats the card name.

## [2.5.8] - 2026-05-30

### Added

- A full achievement catalog page on the site, with search and category
  filters.

### Changed

- `/achievementcatalog` now posts a link to the site catalog instead of a
  long embed list.

## [2.5.7] - 2026-05-30

### Added

- More RB9 library achievements: actor badges, title-theme badges,
  country and genre badges, and new review badges.

## [2.5.6] - 2026-05-29

### Added

- RB9 library achievements for returning films by specific directors,
  actors, franchises, genres, title themes, and extra-long runtimes.

## [2.5.5] - 2026-05-29

### Fixed

- Achievement names with Roman numerals now display correctly.
- `/restart` gives a clearer confirmation message.

## [2.5.4] - 2026-05-29

### Added

- A larger achievement set with more badges for rentals, reviews, games,
  MacGuffins, watchlists, tracking, and Letterboxd.
- An achievement catalog command so admins can post the full badge list in a
  channel.

### Changed

- Achievement unlock posts now use gold embeds with the badge name featured
  at the top.
- Achievement unlocks are checked more consistently across bot features.
- Expanded admin functionality.

## [2.5.3] - 2026-05-28

### Added

- The `mutant mommy` achievement for the holder of the iconic **the
  suckling** MacGuffin.

## [2.5.2] - 2026-05-28

### Changed

- Achievement backfills now post new unlocks to the feed channel.

## [2.5.1] - 2026-05-28

### Changed

- Achievement badge roles now use a matching emoji and title case, like
  `🎬 Poster Child`.

## [2.5.0] - 2026-05-28

### Added

- Achievements: members earn badges from rentals, reviews, MacGuffins,
  games, watchlists, tracking, and Letterboxd linking.
- Watched-movie badges are based on returned rentals; `/return` is how the
  bot records that a member watched something from RB9.
- Members can pin up to 3 earned achievements as visible Discord badge
  roles.
- `/achievements` shows a member's badges and progress hints;
  `/achievementboard` shows recent unlocks and rare badges.
- Admins can set a feed channel where achievement unlocks post.

## [2.4.6] - 2026-05-28

### Added

- `/timezone` sets a member's rental timezone, so rentals are due at 9 pm
  local time.

### Changed

- Rentals are now due at 9 pm on the fifth day instead of exactly 5 days
  from checkout.
- RB9 library checks are faster after restarts and routine updates, using a
  local snapshot of the Plex library.
- `/lb group` output is easier to read, with each linked member's recent
  watches in its own block.
- Letterboxd activity posts now reference the Discord member the account is
  linked to.

## [2.4.5] - 2026-05-26

### Fixed

- Letterboxd activity posts show members' star ratings correctly again.

## [2.4.4] - 2026-05-24

### Changed

- A desktop dashboard for running the bot, checking status, viewing logs,
  and handling updates from one place.
- The launcher guards against duplicate bot starts.

## [2.4.3] - 2026-05-24

### Changed

- Letterboxd activity posting: if one member has more than 3 new logs at
  once, they are combined into one compact post.

## [2.4.2] - 2026-05-23

### Changed

- Rentals now last 5 days.

## [2.4.1] - 2026-05-21

### Changed

- MacGuffin drop posts now show the drop type at the top and emphasize the
  item name.
- Updated one MacGuffin's flavor text.

## [2.4.0] - 2026-05-21

### Added

- Admins can run Plex cleanup checks to find large, rarely watched RB9
  titles that are widely available on streaming services.
- `/plexcleanupnow` previews cleanup candidates or posts them to the
  announcement channel.
- `/plexunpopular` lists low-watch titles with lower TMDB scores.

### Changed

- Rental title matching is more forgiving of punctuation and spacing when
  targeting an active rental.

## [2.3.2] - 2026-05-20

### Added

- `/rent` now offers a choice of rental method: roll random, pick a movie,
  or ask an admin for a recommendation.
- Members can have up to 3 active rentals at once.
- `/myrental` shows all active rentals when a member has more than one.
- `/setrentalrequests` lets admins choose where rental recommendation
  requests post.

### Changed

- `/return` and `/extend` can target a specific rental by id or title when
  multiple rentals are active.
- Randomly rolled rentals have better odds for rare and iconic MacGuffin
  drops on return.
- Watchlist buttons are less likely to show Discord's "interaction failed"
  message after old or expired clicks.
- Movie card buttons, like **+ watchlist**, keep working on newer public
  posts after the bot restarts.

## [2.3.1] - 2026-05-20

### Changed

- Internal reorganization to make future updates easier to ship.
- `/return` no longer requires a rating. A rental can be returned with just
  the recommendation checkbox and optional thoughts.

## [2.3.0] - 2026-05-19

### Added

- MacGuffins: collectible movie objects that can drop when members return
  rentals.
- `/claimguffin` gives each member one starter MacGuffin.
- `/myguffins` shows a member's collection privately, with card details.
- `/giftguffin` transfers a MacGuffin to another member.
- `/adminguffins` lets admins view, add, move, remove, or randomly assign
  member MacGuffins.

## [2.2.0] - 2026-05-19

### Added

- `/botstatus` gives admins a dashboard with bot health, configured
  channels, feature toggles, rental counts, linked Letterboxd count, and
  setup warnings.
- `/lblinked` shows which members have linked Letterboxd accounts.
- Letterboxd activity posting only posts activity from the last 60 minutes,
  so older watches do not flood the channel.

## [2.1.0] - 2026-05-19

### Added

- Linked Letterboxd accounts can feed a shared activity channel when
  members log new watches.
- `/setlbactivity` lets admins choose the activity channel. Posting starts
  from the current feeds, so old watches do not flood the channel.
- `/lbactivitynow` lets admins check for new Letterboxd activity manually.

### Changed

- `/lb tastecheck` now compares any two members or public Letterboxd
  usernames, instead of always comparing from the caller's account.

## [2.0.0] - 2026-05-18

### Added

- Letterboxd linking with `/lb link`, `/lb profile`, `/lb watchlist`, and
  `/lb group`.
- `/lb tastecheck` compares recent Letterboxd taste between two members or
  public Letterboxd usernames.
- Personal watchlists with `/watchlist show`, `/watchlist add`, and
  `/watchlist remove`.
- Movie cards now have a **+ watchlist** button on `/suck`, `/roll`,
  `/rb9`, `/rb9randomscene`, and daily recommendations.
- Films in the RB9 library show a **rent this** button on movie cards.

### Changed

- `/watchlist show` displays 10 films per page and includes a roll button
  for picking from the saved list.
- `/suck` and `/roll` cards include the watchlist and rental buttons when
  available.

## [1.9.0] - 2026-05-17

### Added

- A desktop launcher for running the bot from the Windows tray.
- The launcher can start, stop, restart, show live logs, and update the bot.
- The launcher can be set to start with Windows, so the bot comes back
  automatically after a reboot.

### Changed

- Stopping or restarting the bot from the launcher shuts down more
  gracefully.

## [1.8.0] - 2026-05-17

### Added

- `/extend` adds 24 hours to an active rental, once per rental.
- Rental reminder DMs include an **extend 24h** button.
- `/assignrental` lets admins assign a rental to a member directly.

## [1.7.0] - 2026-05-16

### Added

- `/restart` lets admins restart the bot from Discord.

## [1.6.2] - 2026-05-15

### Changed

- Rental buttons show that the bot is working immediately.
- Rental buttons disable after being clicked, preventing double-click
  issues.

## [1.6.1] - 2026-05-15

### Changed

- Update announcements link back to this changelog page.

## [1.6.0] - 2026-05-15

### Added

- When a new bot version goes live, the bot posts an update announcement in
  the configured update channel.
- Normal restarts do not repeat the same update announcement.

## [1.5.1] - 2026-05-15

### Changed

- Performance and reliability improvements for movie lookups, streaming
  availability checks, RB9 picks, and daily scans.
- The first `/rb9` or `/rent` after a restart is less sluggish.
- No command behavior changed in this update.

## [1.5.0] - 2026-05-15

### Added

- The RB9 rental system.
- `/rent` picks a random film from the RB9 library with 5 days to watch it.
- `/return` returns a rental with a rating, recommendation, and optional
  thoughts.
- Rental reviews post to the configured Discord forum.
- `/myrental` shows the current rental, due date, and review thread.
- `/latefees` shows the late fee leaderboard.
- `/rentalstats` shows rental history and stats for any member.
- `/setreviews` lets admins choose the review forum.
- `/cancelrental` lets admins cancel an active rental without a late fee.
- RB9 movie embeds show a rent button when the film is in the library.
- The bot sends rental reminder DMs before a movie is due and when it goes
  overdue.

### Notes

- Members can have one active rental at a time.
- Random `/rent` picks exclude movies the member has already rented.
- Late fees are $1 per day overdue, calculated at return.

## [1.4.0] - 2026-05-12

### Added

- `/info` shows a public about card for the bot, including version and
  uptime.

## [1.3.0] - 2026-05-12

### Added

- `/play` starts trivia roulette.
- Each round randomly picks a clue type: quote, emoji, tagline, or trivia.
- The first correct guess in chat wins the round.

### Changed

- `/leaderboard` includes wins from both `/guess` and `/play`.
- `/giveup` can end `/play` rounds.
- Guessing games no longer overlap in the same channel.

## [1.2.4] - 2026-05-11

### Changed

- `/watch` was renamed to `/suck`. The lookup behavior is unchanged.

## [1.2.3] - 2026-05-10

### Fixed

- `/roll` respects runtime filters correctly. If no matching movie is
  found, it says so instead of returning one outside the filter.

### Changed

- Internal improvements to movie lookups and availability checks.

## [1.2.2] - 2026-05-10

### Added

- `/watch` shows whether a movie is in the RB9 Plex library.
- If the movie is not in the library, the bot can include a request link.

## [1.2.1] - 2026-05-03

### Changed

- `/rb9genre` counts each film by its main genre for a cleaner genre
  breakdown.

## [1.2.0] - 2026-05-03

### Added

- `/rb9stats` shows overall library stats.
- `/rb9biggest` and `/rb9shortest` show the longest and shortest movies in
  the library.
- `/rb9oldest` and `/rb9newest` show the oldest movie and newest library
  addition.
- `/rb9totalruntime` shows the total runtime of the library.
- `/rb9decade` shows films by decade.
- `/rb9genre` shows the top genres in the library.
- `/rb9randomscene` picks a random film with a backdrop image.

### Changed

- `/plex` was renamed to `/rb9`.

## [1.1.1] - 2026-05-03

### Changed

- `/giveup` works for both `/guess` and `/six`.
- `/six` rounds last 4 minutes instead of 3.

## [1.1.0] - 2026-05-03

### Added

- `/six` starts a six degrees of separation game with two random actors.
- `/sixleaderboard` shows the leaderboard for that game.

### Notes

- Players submit actor-to-movie chains in chat.
- Shorter valid chains score more points.

## [1.0.0] - 2026-05-03

### Added

- First public community version of the bot.
- `/guess` has easy and hard modes.
- `/version` shows the bot version.

### Changed

- Streaming announcements only fire for first-time digital releases.
- Movies moving between services no longer create extra announcement noise.

## [0.9.0] - pre-release

### Added

- `/plex`, the first version of the random RB9 library picker.
- Streaming announcements only announce new availability.

## [0.8.0] - pre-release

### Added

- `/toggle` lets admins turn streaming announcements and daily
  recommendations on or off.

## [0.7.0] - pre-release

### Added

- `/guess` gained movie stills as another guessing mode.
- `/guess` can randomize between poster and still rounds.

## [0.6.0] - pre-release

### Added

- The original `/guess` movie poster game.
- `/giveup`.
- `/leaderboard`.

## [0.5.0] - pre-release

### Added

- `/roll` picks a random horror movie, with optional decade and runtime
  filters.
- Daily horror recommendations can post automatically at noon.
- `/setdaily` and `/dailynow` let admins manage daily recommendations.

## [0.4.0] - pre-release

### Added

- `/track`, `/untrack`, and `/tracked` manage the community watchlist.
- Admins can choose the streaming alert channel.
- Admins can run streaming checks manually.
- The bot checks each morning for newly available movies.

## [0.3.0] - pre-release

### Added

- Persistent bot data, so tracked movies and settings survive restarts.

## [0.2.0] - pre-release

### Added

- `/watch` shows where a movie is available to watch.
- Ambiguous movie searches offer a dropdown to pick the right title.
- `/watch` supports a year option for more specific searches.

## [0.1.0] - pre-release

### Added

- The first `/ping` health check.
- The first `/watch` movie lookup command.
