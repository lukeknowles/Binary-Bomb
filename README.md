Binary Bomb Lab Resources
======

### Bomb Phases Templates
Under `phases-src`, you'll find the different templates which are used to generate randomized phases. Each phase (except for the 7th) has 3 pre-defined variations: a, b, and c. In addition, some values are actually randomly generated/selected and hardcoded into the binary when the bomb is generated. These are identified by constants in the templates (e.g `SOME_STRING_SET`, `POSITIVE_GET`, `LETTER`, etc.)

The entire source code for the lab can be found in `bomblab.tar`. Reviewing how bombs are generated can give you some additional clues, but the phase templates are the most significant thing to have for reverse engineering this project.