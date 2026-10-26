# Screen: team selection

Raj, 25 October 2026. High level behavior for the screen where a user picks and changes their 11.

**Status: behavior agreed, interaction details open.** The rules this screen enforces live in [../game_flow.md](../game_flow.md).

## Principle: conventional mechanics, original look

Raj confirmed this screen's behavior is standard across the apps he already plays. That is deliberate. The selection mechanics follow the convention so anyone arriving from Fanzania or Dream11 is at home immediately. We do not reinvent them.

The design effort goes to two places instead:

1. Making the four bands look genuinely good, rather than white text fighting a busy green field.
2. Showing which of the 11 are playing today versus held for a later match. Neither competitor has to solve this, because neither carries a team forward. It is the one part of this screen with no convention to borrow.

## The current game

The screen knows which game is next, taken from the IPL calendar.

## Default view: the two teams playing

When a user goes to add a player, the default list shows only players from the two teams in the current game. This is the fast path and covers the common case.

The list is band specific. Adding a batsman shows batsmen only, from those two teams. It never shows the full squad and makes the user hunt.

Same for keepers, all-rounders, and bowlers.

## Other teams view

There is a second option to pick from players outside the two teams playing. This is how a user builds ahead for the next two games or more, holding players who are not on the field today.

Within that view the user can filter by team, so they are not flooded with eight teams' worth of batsmen at once.

**Design note.** Raj described this as the alternate option, but by his own account of how the game is played, 4 to 6 of the 11 are playing today and the rest are held for upcoming matches. Users will be in this view constantly. It should not sit behind a secondary or buried toggle.

## Adding and removing

Interaction details are deliberately open and will be worked out later.

- An empty slot in a band shows a plus. Tapping it opens the list for that band.
- Bands only offer as many slots as the cap allows. Batsmen, all-rounders, and bowlers cap at 4, keepers at 2.
- To swap someone out, the user removes the existing player, probably through a minus or similar control.

## Budget: what is selectable

Any player who would push the side past the 100 team value cap is greyed out and cannot be selected. Only players the user can actually afford are available.

**Design note: grey needs a reason.** A player can be unavailable for three different reasons, and all three look the same as plain grey:

1. Their value would break the 100 cap.
2. That band is already full.
3. The side already has 4 international players.

Without a visible reason, an unavailable player reads as the app being broken. Each grey state needs to say why.

**Design note: the stranding trap.** The cheapest player is worth 4.5. A user who fills 10 slots and has 4.0 of budget left has no legal eleventh player and has to go back and undo an earlier pick. The screen should catch this before the user hits the wall, and remaining budget should be visible throughout rather than only becoming relevant at the end.

## Not covered here yet

- The add and remove interaction itself.
- How captain and vice captain get chosen on this screen.
- How a user sees which of their 11 are playing today versus held for a later match. Noted in `../game_flow.md` as the most important thing the screen has to communicate.
- How spending a change credit is shown and confirmed, given each change costs from the 200 tournament allowance.
- What the screen looks like for the very first game of the tournament, when credits are unlimited.
