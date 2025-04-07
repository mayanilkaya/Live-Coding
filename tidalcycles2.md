# tidal cycles 2

## samples

setcps(130/60/4)

hush

d5 $ striate 16 $ s "ann" --16th notes

d5 $ striate 3 $ s "print:0 print:1 print:2"

d5 $ s "bev" # begin 0.55 # end 0.75 --starts at 55% in and ends at 75%.

when you have the sample play by itself it sounds like its overlapping.
it will sound clearer with loop at every ? cycles

d5 $ loopAt 2.2 $ s "ann"

d5 $ loopAt 2.2 $ s "bev"

rachel prefers to use slice instead of striate. takes the sample and chops it
up ? many parts.

from those slices play these parts : "[2 | 4 | 8 | 16]"

d6 $ slice 4 "1 2 3" $ s "ann"

d6 $ slice 8 "0 2 8" $ s "ann"

d6 $ randslice 8 $ s "bev"

* combining loopAt with slice

d6 $ loopAt 4 $ slice 4 "1 2 3" $ s "ann"

* generally it goes from macro to micro so smallest parameter goes last and biggest
parameter goes first.

sample goes last

* effects are serial

once: doesn't live on an orbit because we only call it once

once $ s "xmas"

dollar sign on one level, dollar sign on second, and then effects- to understand the order of operations
this way you can comment out one of the lines and comment them in.

## arpeggiators

arp is pattern for arpeggiator: converge, diverge, pinkyup (pink noise distrubition up),
pinkyupdown( pink noise distrubition down), thumbup (dragging thumb across the pinao), thumbupdown

"<d'major f'hexAeolian af'major"

f for flat
s for sharp

d2
$ slow 2

or

d2
$ fast 2

d2
$ sometimes (fast 2) --sometimes is 50 percent

$ sometimesBy 0.7 (# crush 2) -- sometimes 70 % of the time it's going to be with
crush
