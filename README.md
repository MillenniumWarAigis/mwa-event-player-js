# MILLENNIUM WAR AIGIS EVENT PLAYER [JS]

[toc]

## Introduction

A simple webapp to play back events from the Nutaku version of the game, using the resource files posted on the Wikia.

## Installation

Unzip the resource packs uploaded by Kuremisago on the MWA wikia in a folder of your liking, and copy `event_player.html` in that same folder. You can also customize the paths to the resource files within the webapp.

## Usage

*This player is intended to be used locally on your PC.*

To specify which event to play, either use the file upload input control or drag & drop an event text file directly on the page.

## Controls

`space` or `enter`: go to next utterance or go to end of animation
`mouse wheel`: go to previous or next utterance (not supported in Firefox)
`escape`: toggle menu
`h`: toggle UI

## Parser Extensions

- `#background` **uri**: sets the active background image to **uri**.
- `#music` **uri**: sets the active background music to **uri**.
- `#voice` **uri**: sets the active voice sound to **uri**.
- `#sfx` **uri**: adds **uri** to the sound effects queue.

## Notes

- Lines starting with `//` are ignored.
- Voice and sound effects do not overlap.
- If a voice line and sound effect are present in the same utterance, the sound effects wait for the voice line to finish first before playing.
- Voice effects are randomly chosen and played indefinitely.
- Resources can be precached by prefixing `precache` in front of their name. e.g.:

> // precache resources
  #precache-sfx beep.wav
  #precache-sfx boop.wav
  
>  @Robot
  #sfx <0>
  #sfx <1>
  Beep... Boop... Beep.

- Resource indices can be used instead of URI's. e.g.:

> // queue the first registered sound effect resource.
  #sfx <0>
  // queue the second registered sound effect resource.
  #sfx <1>

- Use `<-1>` to reset a resource to its default state. e.g.:

> // stop any music.
  #music <-1>
  // stop any voice.
  #voice <-1>
  // stop any sound effect.
  #sfx <-1>
