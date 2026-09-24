<p align="center">
  <img src="icon.png" alt="Loresight" width="128" height="128">
</p>

<h1 align="center">Loresight for Foundry VTT</h1>

<p align="center">
  <strong>Say the name. The sheet appears.</strong><br>
  Loresight's live name spotting, running inside your Foundry world.
</p>

<p align="center">
  <a href="https://github.com/furan917/Loresight-foundry-releases/releases">Releases</a> ·
  <a href="https://github.com/furan917/Loresight-foundry-releases/issues">Questions &amp; bug reports</a> ·
  <a href="https://github.com/furan917/Loresight-releases">The Loresight app</a>
</p>

I run games online. Someone says "I cast Rune Ward" or "is that a Cave Ogre?" and I'm the one alt-tabbing through compendium folders while the table waits. Loresight for Foundry is the fix I wanted: it listens to the game, and when it hears the name of anything in your world's compendia, a tile appears in a small window. Click the tile and Foundry opens the sheet. That's the whole trick, and it's a good one.

Everything runs **inside your own browser**. The speech model ships in the module, nothing is sent anywhere, and audio is turned into text the instant it's heard and then discarded. There is no account, no server and no recording.

**Loresight is free and will never be for sale.** If anyone asks you to pay for it, it is not Loresight. The only official downloads are the Releases page of this repository and the Foundry package browser.

This repository distributes the module. The source lives in a separate private repository alongside the Loresight app.

## What it looks like

<div align="center">

<img width="960" height="540" alt="Loresight for Foundry spotting names in a Daggerheart world" src="https://github.com/user-attachments/assets/15bb5c6a-b5a1-4912-9930-b0d919705b8a" />

</div>

That's a Daggerheart world. Someone says "pirate captain", "bear" and "skeleton key" over the course of a scene, the tiles arrive as each one lands, and clicking Bear opens its adversary sheet. There's a short [video](https://github.com/user-attachments/assets/371316a9-58e7-45ac-a7bc-7c44156274b6) of the same session if you'd rather watch it move.

## What it hears

Loresight reads the compendia already in your world. No content ships with the module, so it only knows what you own and have installed. Out of the box it understands:

| System | What gets spotted |
|---|---|
| Dungeons & Dragons 5e | spells, monsters, magic items, conditions, classes, subclasses, class features, and optionally feats, races, backgrounds and rules |
| Pathfinder 2e | spells, creatures, notable items, conditions, class features, feats, classes, actions, and optionally ancestries, heritages, backgrounds and hazards |
| Daggerheart | domain cards, adversaries, environments, classes, subclasses, class features, beastforms, items and consumables, and optionally ancestries and communities |

Any other system gets two generic types, items and creatures, which is still useful. Homebrew and world compendia work like any other pack: if it's in a compendium and the pack is ticked in settings, it can be spotted.

## Installing

1. In Foundry, open **Add-on Modules** and click **Install Module**.
2. Paste this manifest URL into the box at the bottom and click Install:

```
https://github.com/furan917/Loresight-foundry-releases/releases/latest/download/module.json
```

3. Enable **Loresight for Foundry VTT** in your world's module settings.

The download is about 170 MB because the speech model comes with it. That's a one-time install; nothing is fetched after that.

You need Foundry VTT 13 or newer. Listening works in the Foundry desktop app and in Chrome, Edge and other Chromium browsers. Each player who wants tiles turns listening on for themselves; it is not GM-only.

## Using it

1. Click the ear icon under the token controls, or press **Alt+L**. The first time, Foundry will ask for microphone access and Loresight will ask you to confirm that audio stays on your machine.
2. The Loresight window opens and says what it's hearing. Give it a few seconds to load the speech model.
3. Play. Tiles appear as names are spoken, newest at the top. Click one to open the sheet, pin the ones you want to keep, or clear the rest.

**Hearing the whole table.** If your group uses Foundry's built-in voice chat, Loresight mixes in every connected player automatically and the window says "Hearing the table". If you talk over Discord instead, open the module settings and set **Also listen to** to a virtual audio device carrying the call. On Windows and macOS that means installing a virtual audio cable of your choice and routing Discord's output through it. On Linux, run this once before you start listening and pick "Loresight line-in" from the list:

```bash
pw-loopback --name=loresight-linein --capture-props='node.target=<your sink>.monitor' --playback-props='media.class=Audio/Source node.name=loresight_linein node.description="Loresight line-in"'
```

`pactl get-default-sink` tells you the sink name.

**Sharing tiles.** Tick **Share my tiles with other clients** and everyone with the module sees what your client spots. Handy when one person has the good microphone.

**Settings.** Configure Settings, Module Settings, Loresight Settings. Tick the types and packs you want heard, choose a sensitivity (1 is a good default, 2 catches more and guesses more), and pick your microphone.

## Good to know

- Foundry ignores clicks on scene controls while no scene is active. In a world without an active scene, use Alt+L or, from the console, `game.modules.get('loresight-foundry').api.toggle()`.
- Device names in the settings menu are blank until the browser has granted microphone access once. Start listening, then reopen the menu.
- A name mentioned twice in thirty seconds only fires once. The tile is already there.
- Listening costs something on the client doing it: expect the canvas frame rate to dip while the model runs, and about 700 MB of memory while active. Other players and the server are unaffected. Toggle it off between scenes if you notice it.
- Loresight spots names; it does not take notes or transcribe. That lives in the [Loresight app](https://github.com/furan917/Loresight-releases).

## Privacy

Speech recognition runs in your browser, audio is never written to disk or sent anywhere, and the module stores only its settings. See [PRIVACY.md](PRIVACY.md).

---

Loresight for Foundry VTT is proprietary software by [Furan917](https://github.com/furan917). See [LICENSE](LICENSE). Bundled third-party components are listed in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).
