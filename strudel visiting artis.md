##strudel developer visiting artist

###controlling randomness

'javascript

***melody***
const seed = slider(0,0,24,1)
_s :n(irand(12).segment(16).ribbon(seed,1).degradeBy(.2).ribbon(0, 1)
.scale("g minor pentatonic")
.s("sawtooth")._pianoroll()'

#####the ribbon function constraints your pattern into a single cycle which
gives you the same melody over and over again. adding degrade by and ribbon again
so we can constraint it to a single cycle again.

######slider called seed
first argument min, second argument max, fourth argument makes it jump in
whatever increment you put in

######this is helpful if you find a sequence you like and you want to change it up
a little bit

when performing usually starts with a higher degrade value and brings it down,
so the energy goes up, there are more notes.

beat("all the steps you want it to land on",number of steps)

callback function passes the whole pattern into a variable x => x


***beat***
s: s("bd".segment(16).degradeBy(.6).ribbon(15, .5)).bank("mc303")
._punchcard()

s: s('sd').beat("4, 10",16).bank("mc303")
.sometimesBy(" .1", x => x.ply("2 | 4"))

s: s("hh").segment(8).sometimesBy(".25", x => x.ply("2|4"))


######arrange and pick

const chordprogression =
conts piano =
const melody =
...

const sections = [
stack(pad, bell)

]
const arp =
const snare+...
const hat = ...

const parts = [
arp,
kick,
snare,
hat
]

s: pick(parts, "<[arp, kick]@2 [arp, kick,snare]@4 >")




pick allows you to put patterns in an array, and pick them in a pattern

stack(pick(songprogession, sections))
