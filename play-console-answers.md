---
title: Play Console Answers
---

# Play Console declarations for Cap Stars

A crib sheet for the **App content** and **Data safety** sections of the Google Play
Console, written to match the [privacy policy](privacy-policy.md). If the game changes,
change the policy and this page together — a Data safety declaration that contradicts the
published policy is grounds for removal, and the mismatch is what Google checks for.

Cap Stars is **not** the same shape as an offline game, and the reason is online play. On
its own the game is entirely local: career and settings in app-private storage, no network
call made. Online play signs in anonymously to Unity Gaming Services and passes the match
through Unity's Relay. That single feature is what most of the answers below turn on.

---

## Data safety

| Question | Answer |
|---|---|
| Does your app collect or share any of the required user data types? | **Yes** |
| Data type | **Device or other IDs** |
| Collected or shared? | Collected. Not shared with other companies for their own purposes. |
| Purpose | **App functionality** — pairing two players for an online match |
| Is it required? | **Optional.** The whole game except online play works without it |
| Encrypted in transit? | **Yes** |
| Can users request deletion? | **Yes** — by email, see below |

The identifier being declared is the anonymous player ID that Unity Authentication issues
the first time you open online play. It is tied to the app installation, not to a person:
there is no name, email or password anywhere in Cap Stars.

Three things that are **not** collection, in Google's terms:

- **Career and settings saved on the device.** Data that never leaves the device is not
  "collected" for this form. Cap Stars writes your career, match setup and preferences to
  app-private storage, removed on uninstall.
- **Match state passed between two players.** Cap positions, flicks, the score and the
  clock are relayed so both screens agree, held in memory for the length of the match and
  never stored. Google's ephemeral-processing exemption is written for exactly this.
- **The room code.** Six characters issued by the lobby service for one room, not derived
  from anything about the player.

**Confirm this against Unity's own guidance before you submit.** Unity publishes Data
safety guidance for each Gaming Services product, and their list is authoritative for what
their SDK does. If it names a data type this page does not, take theirs.

## App content

| Section | Answer |
|---|---|
| Privacy policy | The URL of [privacy-policy](privacy-policy.md) on this site |
| Ads | **No**, the app contains no ads |
| App access | **All functionality is available without special access** — no account, no login, no region lock |
| Content rating | Complete the questionnaire. Category: Game. No violence, no sexual content, no profanity, no gambling, no drugs, no location sharing, no purchases. **Users interact: yes** — see below |
| Target audience and content | Your decision — see below |
| News app | **No** |
| Data safety | As above |
| Government app | **No** |
| Financial features | **None** |
| Health | **No** |

## Things this page cannot answer for you

**"Users interact" on the content rating questionnaire.** Answer **yes**: two people can
play each other over the internet. Be ready to qualify it accurately — there is no chat, no
messaging, no usernames, no profiles and no way to send text, images or audio to another
player. Interaction is a football match and nothing else, and the two players must already
have shared a room code between themselves. That combination usually keeps the rating where
it would otherwise sit, but the rating boards decide, not us.

**Target age group.** Cap Stars has no ads, no purchases and no chat, so it is technically
clean for any age band. But declaring children among your target audience puts the app
under the **Families policy**, which brings extra review, an age-appropriate design
requirement, and rules about which SDKs you may use — and Unity Gaming Services is an SDK
you would need to check against that list. If you do not specifically want the children's
audience, declaring 13+ is the simpler path.

**How a deletion request actually gets served.** The policy promises that if a player asks,
the anonymous Unity player record will be removed. Decide now how you will honour that:
Unity Authentication has an account-deletion call the app could expose as a button, or you
handle requests by hand through the Unity dashboard. Play will accept an email route for
data this thin, but the promise has to be real. If you add an in-app button, say so in the
privacy policy.

**The INTERNET permission.** Unlike an offline game, Cap Stars genuinely needs it, and it
should be in the manifest. Before submitting, unzip the AAB and read `AndroidManifest.xml`
to see what else Unity added that you did not ask for.

**Have the privacy policy read by someone qualified.** It is written to describe the app
accurately, not to be legal advice, and the liability being declared is yours.
