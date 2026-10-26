# Leagues and getting people in

Raj, 25 October 2026. This is the starting point of the product. Everything in [game_flow.md](game_flow.md) happens after a user is in a league.

**Status: overview, not final.** The shape is settled. Details are open.

## The flow

1. A new user opens the app and creates an account.
2. They start a league. It needs a name and invites.
3. The league is given a unique ID.
4. They invite people by copying a link and sending it themselves through text or a WhatsApp group.
5. Someone who gets the link either creates an account and is added automatically, or, if they already have an account, signs in and is added.
6. Once everyone is in, the league is live. Members can follow the league score, the ranking, and head to head comparisons.

## Admin

The person who creates the league is its admin. The admin can remove people and add more.

## Invites

**Share a link.** The creator copies a link and sends it however they like, usually a WhatsApp group. The link carries the league ID, so opening it puts the person into that league. This works everywhere and needs nothing from the phone.

**Dropped: picking people from the phone book.** Raj asked for this originally and removed it on 25 October 2026. Reading a phone's contacts is a native app capability. A limited version exists in Chrome on Android and Safari on iOS has none at all, so it would be missing for every iPhone user. Recorded here so it does not get proposed again without that constraint in view. Better invite methods can be investigated later.

**On downloading.** The brain dump assumes people download the app before joining. With a web app there is no download and no app store. A person taps the link and is in, and can add the app to their home screen afterwards if they want. The invite flow is therefore shorter than described, not longer.

## League limits

Carried over from the brain dump and not restated since, so treat as unconfirmed: a user can create at most 2 leagues and join at most 2. In practice a group of friends and family usually plays a single league.

## What members can see

- The league score.
- The ranking within the league.
- Head to head comparison, one member against another.

A global leaderboard across all leagues was described in the brain dump as a later ambition, not part of this flow.

## Not covered here yet

- What happens to a member's team and points if the admin removes them mid-season.
- Whether a league can be joined after the tournament has started, and what happens to the credits and games already missed.
- Whether a league has a lock date after which nobody new can join.
- Whether "head to head" here is the same thing as the head to head challenge wildcard in the brain dump, or a separate comparison view.
- What happens to a league if its admin leaves.
