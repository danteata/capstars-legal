# capstars-legal

Public legal and support pages for **Cap Stars**, an Android game published by Digitalix.

Served by GitHub Pages so Google Play has a stable, publicly reachable URL to point at.

| Page | Purpose |
|---|---|
| [`privacy-policy.md`](privacy-policy.md) | Required by Google Play for every app. This is the URL that goes in the listing. |
| [`terms-of-service.md`](terms-of-service.md) | Not required by Play, but standard and cheap to have. |
| [`support.md`](support.md) | Backs the support contact in the listing. |
| [`play-console-answers.md`](play-console-answers.md) | Crib sheet for the App content and Data safety sections, kept consistent with the policy. |

## Before the listing goes live

- [ ] **Replace every `CONTACT_EMAIL_HERE`.** It appears in the privacy policy, the terms,
      the index and the support page. The listing cannot go live with the placeholder in
      it, and a privacy policy with no working contact address is non-compliant.
- [ ] Confirm **Digitalix** is the name you want on record as publisher and data
      controller. If it is not a registered entity, naming a person is the safer choice.
- [ ] Decide how a **deletion request** is actually served — see
      [`play-console-answers.md`](play-console-answers.md). The policy promises one.
- [ ] Check the Data safety answers against **Unity's own published guidance** for
      Authentication, Lobby and Relay. Theirs is authoritative for what their SDK does.
- [ ] Have someone qualified read the privacy policy. It is written to describe the app
      accurately, not to be legal advice, and the liability being declared is yours.
- [ ] Check the date at the top of each document still makes sense when you publish.

## Keeping it true

The policy rests on facts about the build that a future change could quietly break.

Offline, and true today:

- career profile, last match setup and preferences go to `PlayerPrefs`, which is
  device-local and removed on uninstall
- Unity Analytics, Ads, Purchasing, Cloud Diagnostics and Performance Reporting are all
  disabled in `ProjectSettings/UnityConnectSettings.asset`
- the only text a player can type anywhere in the game is the room code, and
  `RoomCode.Normalize` restricts it to letters and digits

Online, and the reason this policy is not RollAm's:

- `Assets/CapStars/Scripts/Net` uses Unity Gaming Services — `NetSession` signs in through
  `SignInAnonymouslyAsync`, `NetLobby` holds the room, `RelayLink` carries the match
- no display name, no profile and no chat exist anywhere in that code

What would make the policy false: adding an analytics or crash-reporting SDK, adding chat
or player names, adding a leaderboard or cloud save, adding ads or purchases, or storing
match results on a server. Change the policy and
[`play-console-answers.md`](play-console-answers.md) in the same commit as the change that
breaks it, and update the Data safety form before that build ships.
