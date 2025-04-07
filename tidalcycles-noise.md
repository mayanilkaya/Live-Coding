# tidal cycles noise patch

i looked up tidal cycles tutorial and went to the first video that popped up.

[https://www.youtube.com/watch?v=vMT4Ux-yVdU]

my first step was to get 2-3 samples that weren't too complicated. I started with
a 909, wobble, and bleep. I found some drum loops that were in the folder fm,
that i wanted to use but didn't know how yet.

i started out with the effects we used in class, and created a layer that i liked with the 909 and hihats.
i found a folder called bleep that i thought would sound cool with crush and distortion.

with everything i have so far, i felt like i was going to more of a noise direction.

i needed a low frequency heavy bass so i added wobble and some effects. i like how
the filter with ' sine ', and varying parameters of crush create variety.


next i added a random loop from the fm folder. i thought it would be cool if i distorted
them so much that it was just rhythmic noise. i didn't really add distortion or crush,
but i got a nice effect with squiz. changing the filter would be a nice variation while performing.

my last addition was my last line d6 space. i was looking for a rhythmic counterpoint
with a noisy/industrial texture so i got this sampple and told it to repeat 40 times with random
silences which already changed the texture towards something that I wanted more. and then i added
the squix and crush effects. i found out about freeze on the documentation website,
i'm not really sure if it is doing anything but i was trying it out.

here it is:

'javascript
d1 $ sound "wobble!30?" # djf sine # delay "1" # crush "[2| 16 | 4]"
d1 silence

d2 $ sound "909!16?" # djf sine # delay "1"
  d2 silence

d3 $ sound "hh!16?"
  # djf sine
  # squiz "6"
  d3 silence

d4 $ sound "bleep:7!20?" # crush "4" # distort "1" # djf sine
d4 silence

d5 $ sound "fm:4" # squiz "10" # lbrick sine
d5 silence

d6 $ s "space:2*40?" # squiz "[2 | 8 | 10 | 16]" # hbrick sine # freeze "1"
d6 silence
'
