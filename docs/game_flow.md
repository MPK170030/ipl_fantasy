# How a game is played

Raj, 25 October 2026. High level overview of the flow a user goes through to play one game.

**Status: overview, not final rules.** The shape below is settled enough to design screens against. The exact numbers, the scoring table, and the full wildcard list are still to be worked through. See [brain_dump.md](brain_dump.md) for the raw thinking behind it.

## The flow

1. User opens the app.
2. First time in the tournament, the user builds an 11 from scratch. The first game is unlimited credits.
3. After that the user carries the same 11 forward and changes players as the tournament goes on. Each change costs a credit from their tournament allowance.
4. User locks the team in before the game starts. Changes made after the start do not count.
5. The game is played. Players earn points based on what they actually do on the field.
6. Wildcards, if played, change how those points are multiplied or counted.

## Picking the 11

Every team is exactly 11 players.

**Cost.** Each player costs between 4.5 and 10. The 11 together must come to 100 or less.

**Category minimums and maximums.**

| Category | Minimum | Maximum |
|---|---|---|
| Wicket keeper | 1 | 2 |
| Batsman | 1 | 4 |
| All-rounder | 1 | 4 |
| Bowler | 1 | 4 |

At least one of every category. The caps add up to 14, so no single category can fill the side and the user has to find their best balance within 11.

**International players.** Maximum 4 in the playing 11, counted across all categories, matching the real IPL rule.

## Two separate numbers

These are easy to confuse. They are not the same thing and they do not trade against each other.

**Team value: 100.** This is the combined value of the 11 players in the side. Each player is worth between 4.5 and 10. The eleven together must never exceed 100. Worked example: ten players chosen come to 95, so the eleventh has to be worth 5 or less. Eleven players at the 4.5 floor is 49.5, at the ceiling 110, so 100 is a real constraint without being punishing.

**Tournament credits: 200.** This is the allowance for changing players over the whole tournament. One credit buys one player change. With 80 or more games in a season, that is roughly two and a half changes per game on average, so credits have to be spent carefully.

The first game of the tournament is unlimited credits, so the opening 11 can be built freely.

Both limits apply at once. A change has to leave the side within 100 as well as within the remaining credits.

## Which of your players score on a given day

The 11 can be drawn from any of the ten IPL teams. It is not limited to the two teams playing today.

Only the players who are actually on the field that day score. In practice a user will have roughly 4 to 6 of their 11 playing in the current game, with the rest held for matches coming up.

This is deliberate and it is where the strategy lives. Holding players who play tomorrow and the day after means fewer changes, which means fewer credits spent. A user who rebuilds for every single match will run out of credits long before the season ends.

Design consequence: the main screen has to make it obvious at a glance which of your 11 are playing today and which are waiting for a later match. That split is the single most important thing a user needs to see.

## What other users can see

Opponents' teams are never hidden outright. They are shown one game behind.

Before the current game starts, looking at an opponent shows the team they fielded in the **previous** game. The moment the current game starts, it switches to their current team and everyone can see what they did.

The point is to stop users copying each other's selections. A user's changes stay private until they no longer matter.

Two consequences:

- **Data.** A frozen copy of every team has to be kept as it stood at each game's lock, not just each user's current team. The previous game's lineup is what everyone else is looking at. Building this as a single current team makes showing the previous one impossible later.
- **Design.** It has to be unmissable which game a team belongs to. Someone who mistakes last game's lineup for the current one will reason from the wrong information.

This also makes the game more interesting rather than less. A user can see a rival's last 11 and knows roughly how many changes they can afford, so they can reason about what the rival has probably done.

## Wildcards

One wildcard at a time. The user can play it whenever they choose during the regular season.

## Not covered here yet

These are not gaps in Raj's thinking, just things this overview does not reach:

- The points table: what each run, wicket, catch, and milestone is worth.
- Captain and vice captain multipliers.
- The full list of wildcards and what each one does.
- What happens when a match is cancelled or abandoned.
- Leagues, invites, and leaderboards. Those are a separate flow from playing a game.
