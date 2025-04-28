I really liked the glitch folder in the samples so i wanted to create a patch mostly using them.

i created a beat by using the random function, and layered 2 of them with different variations:

d5 $ n ("1 ~ 2 [3 2] ~ 2" |+ irand 16) # s "glitch" # djf sine # krush 10 # delay 1 # gain 3 # binshift 0.3
d5 silence
-- ^vary lbrick and djf add delay
d6 $ n ("2 ~ 1 [4 2] ~ 3" |+ irand 16) # s "glitch2" # lbrick 1 # delay 2  # gain 1.3
d6 silence


I have seperate lines for different sounds in the glitch folder as hihats:

d1 $ struct "f(5,8,3)" $ degradeBy 0 $ sound "glitch2:2?" # coarse 5 # lbrick "<1 0.5>" # delay "< 0 0.5 1> " # gain 1

d3 $ struct "f(5,8,3)" $ degradeBy 0 $ sound "glitch:2?" # coarse 3 # lbrick 1 # delay "<1 1.5>" # gain 0.6

there's a sample that i really liked and used it as a pad, and changed its pitch with the accelerate function.

d2 $ struct "t(12,20)" $ sound "glitch:5!16?" # delay "<0.5 1.5>" # djf "<0.5 0.7>" # gain "0.7" -- # accelerate "< 0 0 0.1 0.1>"


this was my kick:
d7 $ struct "f(12,20)" $ degradeBy 0.1 $ sound "glitch:1?" # delay "1.5" # djf sine # gain 1

i'm going to be changing the filters and the values so that the same sound can shift to different types of timbres.

this was creating the beat.

for rest of the pads and pitch based stuff;

d8
$ degradeBy 0.9
$ often (fast 20)
-- 40 60 20
$ rolledBy sine
$ n "<d7'sevenSus4'o d7'sevenSus4'o d7'sevenSus4'o c6'min9'o>"
  --  c7'min9'o"
# sound "gabor"
-- # sound "superpwm"
# binshift 0.2
# accelerate 0.1
-- ^ vary
# krush 10
# hbrick sine
# waveloss 2
# tremolorate 40
# delay 20--  vary
# gain 0.5
# room 20

i created this chord progression and found it was useful to change parameters in order to add varioaton.
especially changing the speed a drastic amounts adds a lot of variety, and it reminded me of a no input
mixer when it's super fast.

i liked the gabor sound the most out of the synths.

and then i added noise, which technically is a part of the beat because it's so rhythmic :

i think i created the rhyth,s by varying the speed, and a high delay amount.

i'm not sure if the chords did anything, but i wanted to keep them the same incase i wanted to
exchange supernoise with another synth.

d9
$ degradeBy 0.7
$ often (fast 4)
-- 40 60 20
$ rolledBy sine
$ n "<d7'sevenSus4'o d7'sevenSus4'o d7'sevenSus4'o c6'min9'o>"
  --  c7'min9'o"
# sound "supernoise"
-- # sound "superpwm"
# binshift 0.2
# accelerate 0.5
-- ^ vary
-- # krush
# waveloss 2
# tremolorate 0
# delay 5
# gain 0.5
--  vary
d9 silence
