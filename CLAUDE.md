# IPL Fantasy

Facts only. Working rules live in Raj's global file, not here.

## What it is and who it's for

A fantasy cricket league app for the Indian Premier League. Phone first, also works on desktop. Built to replace Fanzania and Dream11 for Raj's circle: friends and family, invited by a league code.

Free to play. No money involved, no prizes, no payments. Entertainment only.

Built so it can grow past one league if it works, but the first audience is a private group.

Current state: starter project only. The screens, the database, and the live score feed do not exist yet.

## Who is building what

Two builders.

- **Manav (MPK170030)** owns the repo and the live cricket score data: where scores come from, what it costs, how it gets in.
- **Raj (rp3extras-prog)** owns product and design.

Each works on their own branch, then merges to `main`. `main` is shared, so nothing gets pushed there without Raj saying so for that specific push.

## How to preview, build, and deploy

The project uses `pnpm`, which is not installed on Raj's machine yet. It has to be installed once before any of the below will work.

| What | Command |
|---|---|
| Install the supporting packages | `pnpm install` |
| Preview on localhost | `pnpm dev`, then open http://localhost:3000 |
| Build | `pnpm build` |
| Check for code problems | `pnpm lint` |

Node 24.15.0 is installed and is current enough.

There are no tests yet.

Deploy target is not confirmed. Vercel is the obvious fit for this kind of project and matches Travel Planner, but nothing is connected yet. Manav's call to confirm.

## Folder map

| Folder | What's in it |
|---|---|
| `app/` | The pages people see. `page.tsx` is the home screen, `layout.tsx` wraps every page, `globals.css` holds the base styling. |
| `components/ui/` | Reusable interface pieces (buttons and so on), from the shadcn set. |
| `lib/` | Small shared helpers. |
| `public/` | Images and icons served as-is. |
| `docs/` | Product decisions and raw material. See below. |
| `docs/screens/` | One file per screen, describing how it behaves. |
| `reference/` | Competitor screenshots and research. Local to Raj's machine only, deliberately kept out of the repo. |

## Documentation

Decisions live in `docs/`, the same way Travel Planner works. If it is not written down in a file, it is not decided.

- `docs/league_flow.md` holds the starting point: creating an account, starting a league, inviting people, and what league members can see. Read this before `game_flow.md`.
- `docs/game_flow.md` holds the high level flow for playing a game: team size, category limits, the 100 team value cap, the 200 tournament credits for changing players, and the international cap. Settled enough to design screens against.
- `docs/screens/` holds one file per screen. `team_selection.md` covers picking and changing the 11.
- `docs/brain_dump.md` holds Raj's original unedited brain dump from 25 October 2026. It is raw material, not decisions. The rules in it are not final and are not to be treated as settled.

The scoring table, the full wildcard list, and the league and leaderboard flows still have to be worked through properly in a dedicated session.

## Tech choices

Chosen by Manav before Raj joined. Same family as Travel Planner, so the habits carry over.

| Piece | What it is in plain terms |
|---|---|
| Next.js 16 | The framework the whole app is built on. Handles pages and loading speed. |
| React 19 | What the screens are actually made of. |
| Tailwind 4 | How things get styled. |
| shadcn and Base UI | A ready-made set of buttons, menus, and dialogs to build on, so basic pieces do not get built from scratch. |
| Lucide | The icon set. |
| TypeScript | Catches a class of mistakes before the app runs. |
| pnpm | Installs and manages the above. |

Not chosen yet: where accounts and leagues get stored, how people sign in, and the live score source.

Not set up yet: the progressive web app layer. Raj asked for a PWA, meaning people can add it to their home screen and open it like an app. As of Manav's first commit there is no manifest and no service worker, so it currently behaves as an ordinary web page. Small piece of setup, but it is not there.

## Connections

| Thing | Where |
|---|---|
| Repo | https://github.com/MPK170030/ipl_fantasy (public) |
| Hosting | Not connected yet |
| Database | Supabase. Stores players, player values, users, leagues, teams. Also handles sign in. |
| Score data | None yet, Manav's call |

The repo is public. Any paid data feed key must go in the hosting provider's settings, never into the code. Password and key files are already excluded from the repo.

## Project-only facts

- Raj and his group have been playing this fantasy league together for 19 years. The rules are not being invented here, they are being moved into an app. When a rule sounds oddly specific, assume it got argued over and settled years ago. Ask before treating one as arbitrary or improving it.
- The IPL is a T20 tournament: 20 overs a side. Ten teams, split into two groups of five. Each team plays 14 league matches, giving 70 league games, plus 4 playoff matches (Qualifier 1, Eliminator, Qualifier 2, Final). 74 matches in total. Verified October 2026.
- The season runs from late March to the end of May, about nine weeks. IPL 2026 ran 28 March to 31 May. The next season is IPL 2027, which means roughly five months from October 2026.
- Each team therefore plays every four or five days. This is what makes holding players for upcoming matches a workable strategy. If teams played less often, banking players would not work.
- Only 2 of the 10 teams play on any given day, one or two matches daily. This shapes how team building has to work.
- Raj's brain dump assumed 80 or more games. The real figure is 74. Worth checking the 200 credit allowance against the true number before it is locked.
- **Target season is IPL 2027.** Starts late March 2027, so that is the hard deadline.
- The IPL player auction is in December 2026. Squads are not known until then, and the full confirmed squads land roughly a month before the tournament, so around February 2027.
- This does not block design or build. Screens get built against placeholder players and the real squads are swapped in once they exist.
- Every player needs a value between 4.5 and 10. That is roughly 250 players across ten squads, and it cannot be done before the auction. **Raj sets these values himself**, not the data feed and not Manav. He will need a way to enter them in bulk and to adjust one mid-season.
- Scoring is meant to lean toward bowlers. T20 heavily favors batters, and the point of the custom scoring is to correct that.
- Player photos are licensed images. Using real ones on a public app is a copyright question, so either the data feed includes them or the app uses its own illustrated player cards.
- Fanzania's published rules are at https://www.fanzania.com/Home/Howtoplay/ and are a useful reference point to argue with, not a template to copy.

## Open questions

1. Whether the deploy target is Vercel.

## Known risks

- **Team privacy has to be enforced by the database, not the screens.** Opponents' teams are shown one game behind until the current game starts. See `docs/game_flow.md`. In Supabase each person's app talks directly to the database, so the permission rules decide what they can read. If those rules are loose, a technically minded player can read rival teams before lock while the app looks completely normal. This is the most common Supabase mistake and it lands on the one rule the game cannot lose. Write it carefully, then test it by actively trying to peek.
- **Teams must be stored as a frozen copy per game, not just a current team.** Everyone sees the previous game's lineup, so that snapshot has to exist. Cheap to build in now, painful to retrofit.
- Free Supabase projects sleep after roughly a week of inactivity. The off-season runs June to March, so it will sleep. Waking it is trivial but it should not be mistaken for the app being broken. Not fully verified.
- Live scoring is the one place cost could creep. Points should be worked out once centrally and sent to everyone, rather than every player's app calculating its own. Irrelevant at family scale, relevant at the 100 player global league Raj described.
