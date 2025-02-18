# LC week 3 notes

** May Rose is coming Monday March 3rd. **

** Visualist live coding artist Char Stilles is coming on Monday April 28th. **

** try to have your final almost done, wednesday the 23rd of April because there will be
a visiting artist the next class **

## patterns

### sequencing

- n is used for sample and note, they're used interchangeably. but you can't use n and note
in a single or
orbit.

if synths are our source of sound, then n and note means the same things. we still
can't mix them within a single line.
but pitch names and scale degrees can be used interchangeably.

it's default scale is C, so 0 is C.

you can define your synthesizer with pitch name 'c' and octave '4':c4

'javascript note ("[c4, d3, e4]").sound("sine")'

*everything we did for the percussion patch, reapplies.

`javascript n("0 2 4 6 4 2").scale("C:major").sound("sawtooth")`

*if you're using scale, you have to use 'n'.
note' won't work.

* 12 semitones in a scale so range(0,12) will make it chromatic. segment (8) will segment
it into 8 steps so that we have an eight step sequencer: *

`javascript n(rand.range(0,12).segment(8)) .scale("C:major") .s("sine")``

[what i did in class](https://strudel.cc/?ZEmMgjOGRsWy) :
`javascript n(rand.range(0,12).segment(8)) .scale("d:mixolydian") .s("sine").fast(2).slow(square)`

**tried to stack but couldn't make it work, come back to it.

### sample transformations

#### loop at

changes the speed, therefore changes the pitch.

#### begin

comands where to start the sample. you can give it
oscillatior comander inputs--random beginning points. (this didn't
work in class so we found another solution down below)

begin("<0.5 0.75 0.25>")

<a b> means ababababab

begin is a percentage between 0 being beginning and 1 is end.

if rave is our sample; (this is to make our starting point of the sample
randomized)

s("rave").begin.(rand.range(0,1))

### sophisticated pattern transformations

#### degradeBy

s("hh*16").degradeBy(0.8)

this means 80 percent of the time, it's going to be dropping out.
like a more elaborate version of the '?'

#### struct

takes a boolean structure, and applies it to the pattern.

x are true, ~ are false. it will play when it's true, and not when
it's false:

javascript 'note("c,eb,g") .struct("x ~ x ~ ~ x ~ x ~ ~ ~ x ~ x ~ ~") .slow(2)'

#### mask

another way of using boolean transformations, with shorthand.

'javascript note("c [eb,g] d [eb,g]").mask("<1 [0 1]>")'

*you don't need pipe notation | here, to say true or false, because it's boolean
already.

1 is true and 0 is false.
first cycle true, second cycle true or false randomly, repeat.

#### palindrome

plays your thing backwards.

#### linger

linger takes the argument of somewhere 0 to 1 where 1 is the end and 0 is
the beginning of your patter, or sample.
And it sits there until the next part of the cycle.

*** useful for drum breaks ***

#### euclidian rhythms

javascript `note("c3").euclid("<7,5>, 16")`

-quantizing polyrhythms

-try experimenting with 4 division lowers, and odd numbers as 'denominator'
