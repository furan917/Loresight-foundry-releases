# Loresight for Foundry VTT Privacy Policy

_Last updated: 2026-09-24_

Loresight for Foundry VTT is a Foundry module that spots spoken names and opens the matching
compendium entry. It is designed so that everything happens **in your own browser**.

## The short version

- **No accounts. No servers. No network.** The module has no backend and makes no requests of its
  own. The speech model ships inside the module and is fetched once from your Foundry server.
- **We do not collect, transmit, sell, or share any personal data.** There is no analytics, no
  telemetry, no advertising, and no third-party tracking.
- **Nothing you say is stored.** Audio is processed in memory and discarded. The module keeps no
  transcript.

## Microphone and other audio

- Your microphone is used **only while you have turned listening on**, and the Loresight window
  shows what is being heard the whole time.
- If your world uses Foundry's built-in voice chat, the other players' audio that Foundry already
  delivers to your browser is mixed in. If you configure an extra input device, that device is
  opened as well. Both stop the moment you toggle listening off.
- Audio is **processed entirely in your browser** by the sherpa-onnx speech engine. It is **never
  uploaded** anywhere and **never written to disk**.

## What the module stores

Only its settings, in Foundry's client settings for your browser: which types and packs to spot,
sensitivity, your chosen input devices, whether you share tiles, the tiles window position and
whether you have acknowledged the microphone notice. Nothing else.

## Sharing tiles

If you tick "Share my tiles with other clients", the name and compendium reference of each spotted
entry is sent to the other connected players through your Foundry server's own socket. No audio
and no transcript is ever sent.

## Contact

Questions go to the issue tracker of this repository.
