#strudel percussion patch

i started with the example on github as a template because it
was easy to see the code as a 16 step sequencer like we talked
in class.

The first thing I did was try to mess up the groove, because I
didn't want to have something that was playing a steady groov e, and wanted
to lean towards more on a glitchy sound.

To do that I added some bd, hh, sn in random spots and gave them different
amounts of repeats. I added a new line with clap and rim using |, so that
it wouldn't get too dull repeating the same thing all the time:

`javascript
stack( "[~ ~ ~ ~] [~ bd ~ ~] [~ bd bd ~] [~ ~ bd!8, bd!3] ",
       "[~ ~ ~ ~ | ~ sn!36? ~ ~ | ~ ~ ~ ~ | ~ ~ ~ ~] ",
       "[~ ~ ~ ~] [~ ~ ~ ~] [~ ~ ~ ~] [~ ~ rim!12]",
       "[~ ~ hh ~] [~ ~ hh!2,hh!3 ~] [~ ~ ~ ~] [hh ~ hh!16 ~] ",
       "[~ ~ ~ ~] [cp ~ ~ ~] [~ ~ cp ~] [~ ~ ~ ~] ",
       "[~|cp!40| cp |rim!5?]",
       "[bd!30 ~ ~ ~]",
     ).s().fast(5)
`

I sped up the tempo for fun, and didn’t like that it was always playing the same beat and wanted to get rid of the groove. So I got rid of the brackets on the second line for the snare drum and aded | to make it get out of that groove
. Also got rid of hh!90 just because I thought it was making an ugly sound.

And then I played around with finding the noises that I thought didn’t work in the patch. It sounds like a metal song now haha. going to speed the tempo higher to make it noise.i’m playing around with the tempo, seeing how it’ll sound like at random paces. I also wanted to see how the timbre would change if I said repeat 300 times etc for the rim and I think it’s interesting the pallet of noise you get just y hanging the amount tf repeats.

You can get pitches when you do bd!10 for example and the pitch rises when you rise the number of repeats. At !500? It does a cool glitchy kick.

I got rid of the kicks cause it felt like the groove was too obvious which I didn’t want it to be.  And found out that it can get really glitchy when you put a high number of repeat with random silence together with another sound source and do the same for it. Like : co!100? Bd!200?

I played round with that idea a little more and made fast.(2) to (sine). I like how scattered it sounds now. When I pit in 2 it doesn’t sound bad either but it gets boring because it’s always repeating the same thing but the sine makes it more interesting. I want to find ways to make it not so repetitive. 3 is also cool

To make other patterns I tried making fast(2). Randomized by sine wave and making that 6 times faster.

`javascript
stack( "[~ ~ ~ ~ ] [~ sn!3,sn!7 ~ ~ ] [~ ~ ~ ~ ] [~ ~ ~ ~] ",
       "[~ ~ ~ ~] [~ ~ ~ ~] [~ ~ ~ ~] [~ ~ ~ ~]",
       "[~ ~ hh!30 ~] [~ ~ hh!2,hh!3 ~] [~ ~ ~ ~] [hh ~ hh!160? ~] ",
       "[~ ~ ~ ~] [cp ~ cp ~] [~ ~ cp ~] [~ ~ ~ cp!3] ",
       "[cp!100? bd!200? ] [~ ~ ~ ~]  [rim!120? hh!200?] ",
     ).s().fast(2).fast(sine).fast(6)
`

And then I did this:      ).s().fast(2).fast(square).fast(sine)
I like this patch right now because there's an odd time feel to it with the randomized kicks,
everything else that is multiplied 100s of times is producing a pitch, so there's
an odd melody as part of the beat:

[current patch](https://strudel.cc/?Jme0eSCA61qd)
