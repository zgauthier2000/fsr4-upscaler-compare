# FSR 4 upscaler comparison

Slider pages comparing upscalers on frames recorded from real games: AMD FSR 4.1.1, AMD FSR 4.1.2 Lite, the upcoming builds of
[fsr4-shader-performance-overrides](https://github.com/zgauthier2000/fsr4-shader-performance-overrides), FSR 3.1, HelixSR 2.0 and XeSS.

**Open the pages:** https://zgauthier2000.github.io/fsr4-upscaler-compare/

| Set | Game | What to look at |
|---|---|---|
| `stellarblade-shield` | Stellar Blade (demo) | a warship over the planet in the opening: engraved hull, debris, tracers |
| `stellarblade-armor` | Stellar Blade (demo) | EVE leaving the escape pod in the opening: glassy shards, ponytail, sparks |
| `stellarblade-pods` | Stellar Blade (demo) | escape pods spiraling down through the clouds: pods, debris, streaks |
| `sottr-stairs` | Shadow of the Tomb Raider | distant stairs and railings: thin lines that crawl |
| `sottr-jungle` | Shadow of the Tomb Raider | the jungle path: dense leaves, hanging vines, fog |
| `wukong-bridge` | Black Myth: Wukong Benchmark Tool | the bamboo bridge: thin railings, foliage, rock |

## These are not game screenshots

Each picture is an upscaler's raw output from the same recorded game frames. A small recording layer between OptiScaler and the
upscaler saved what the game handed to the upscaler: the rendered picture before upscaling, depth, motion vectors, camera jitter,
exposure and frame timing. Every upscaler was then run on those same frames, from the same start, so two pictures differ only by
the upscaler.

The game's tone mapping, color grading, bloom, film grain, sharpening and UI are not applied (they run after the upscaler in the
game). The output is shown with one plain display mapping for all pictures, x/(1+x) then gamma 2.2, so colors differ from the game.

- AMD FSR 4.1.1 and FSR 3.1 ran through AMD's own library, HelixSR 2.0 through its own library, XeSS through Intel's SDK library.
- AMD FSR 4.1.2 Lite and the upcoming builds ran in this project's local test harness, not AMD's own runtime.
- The upcoming builds are unreleased. 4.1.2-lossy and 4.1.2l-lossy are lossy: they change the picture to run faster.

## Timings

The time beside each name is one upscale to 3840x2160 (from 2260x1272, a moving scene), measured on an RX 7800 XT under Linux
(Proton) with the project's timing program, not taken from these clips. XeSS was timed with GPU timestamps around each call in a
separate test program, at the same sizes. Timings will differ on Windows, and between GPUs: a different card can rank these
upscalers differently.

## Files

- `site/index.html`: the slider page (`?set=<name>&a=<n>&b=<n>` picks a set and the two pictures). "Add images" compares your own
  pictures in your browser; nothing is uploaded.
- `site/sets/<name>/`: lossless WebP frames and `set.json` of each set.
- `tools/mkcompare.py`: makes a set from upscaler output frames.

Game pictures belong to their games' publishers and are shown for comparison. The raw recorded inputs are not published.
