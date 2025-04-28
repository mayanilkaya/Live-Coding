tidal notes 3

advanced patterns

synths in supercollider

supeprchip
superreese
hammond

you can go through different voices/

d4 $ n"0 2 4 6 0 2 6 8"
# s "superhammond"
# voice 2

--granular synth

d6 $ n "0 2 4 6 8"
# s "gabor"

to get chords listed
import Sound.Tidal.Chords
chordList

rolledBy determines when to hit on different parts of the chords
d1
$ often (slow 16)
$ rolledBy sine
$ n "c'min9'o" -- 'o' makes it strum like an open tuning on the guitar
# sound "cyclo"

d1
$ segment 16
$ note (scale "chromatic" $ floor <$> (range 0 16 sine))
# sound "gabor"

hocketing

d7 $ off 0.5 (# squiz 4)
$ n ("~ 7 2 [3 2]" |+ irand 6) # s "gabor"

for multichannek : spin

d7 $ spinp 3 # n ("~ 7 2 [3 2]" |+ irand 6) # s "gabor"



divide the pulse of the cycle into 4:

d1 $ s "{bd cp hh}%4"

d1 $ s "{bd cp hh}%8"

the 3rd number is shifting around where the quantizing is happening so its offsetting\
d1 $ "e(5,8,0)" # s "reverbkick"

d1 $ "reverbkick(5,8)"

or

d1 $ euclid 5 8 $ s "reverbkick"

first argument is events, second argument is steps per cycle

d1 $ distrib [9,16] $ s "reverbkick"

d1 $ distrib [9,16,"<5 3>"] $ sound "reverbkick"

first its choosing 5 of the 9 to play, then 3 of the 9 to play

you can take the lower range aiwth a floor function, and have the top of the scale be the values on the right:

d1
$ segment 16
$ n (scale "minor $ floor <$> (range "<0 4 -8" "<12 14 13 -13>" sine))
# sound "superhammond"
# legato 0.5
# lpf 1000
# lpq 0.1

struct tells it when to play. every 3rd pulse within 5, play. (t stands for true)

d1
$ struc "t(<3 5>,8)"
$ n (scale "minor" $ floor <$> (rane "<0 4 -8>" "<12 14 13 -13>" sine))
# sound "superhammond"
# legato 0.5
# lpf 1000
# lpq 0.1


d1 $ segment 16
$ n (scale "minor" $ floor <$> (slow 2 $ (slow 2 sine + slow 3 cosine) * "<6 -3>"))
# sound "superhammond"
# legato 0.5
# lpf (range 400 5000 saw)
# lpq 0.1

this with struct and off


d1
$ off 0.25 (|+ n12)
$ struct "t(<9 7>, 16)"
$ segment 16
$ n (scale "minor" $ floor <$> (slow 2 $ (slow 2 sine + slow 3 cosine) * "<6 -3>"))
# sound "superhammond"
# legato 0.5
# lpf (range 400 5000 saw)
# lpq 0.1

nice way of making good bass lines etc

d1 $ struct "t(3,8)" # sound "wobble"
d2 $ struct "f(3,8)" $ sound "gabba:4"

clearer when:

d1 $ stack [struct "t(3,8)" $ sound "gabba:4",
            struct "f(3,8)" $ sound "gabba:5"
            ]

stitch is shortcut for this:

d1 $ stitch "t(3,8)" (sound "gabba:4") (sound "gabba:5")

mask is another type of boolean function.

FINAL is due next week.

if you have hydra installed you can use it.

if you want to use it, to integrate it into pulsar
--i dont have node.js on my computer so it's not working.
