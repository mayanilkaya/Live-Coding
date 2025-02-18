# strudel patch #2 documentation

I wanted to create a stack, but realized that I didn't quite understand
how to with 'note'.

I clicked on shuffle so I could see how other people were stacking melodic lines and I saw they were using "$".

This is how I arranged my patch at first:

`javascript
$: n(rand.range(0,12).segment(3)).scale("D3:mixolydian") .s("sine").fast(100).fast(sine).gain(0.2)

$: n(rand.range(0,12).segment(8)).scale("D5:mixolydian") .s("sine")
//bass
$: n(rand.range(0,12).segment(9)).scale("D1:locrian") .s("sine").fast(2).gain(5)

$: stack(
  "[~ ~ ~ ~ ] [~ sn!3,sn!7 ~ ~ ] [~ ~ ~ ~ ] [~ ~ ~ ~] ",
  "[~ ~ ~ ~] [~ ~ ~ ~] [~ ~ ~ ~] [~ ~ ~ ~]",
  "[~ ~ hh!30 ~] [~ ~ hh!2,hh!3 ~] [~ ~ ~ ~] [hh ~ hh!160? ~] ",
  "[~ ~ ~ ~] [cp ~ cp ~] [~ ~ cp ~] [~ ~ ~ cp!3] ",
  "[cp!100? bd!200? ] [~ ~ ~ ~]  [rim!120? hh!200?] ",
).s().fast(sine).gain(0.050)`


I was using my previous 'percussion' patch as a beat example for this one.

## I'm messing around with different ideas using one main code which is
n(rand.range(0,12).segment(3)).scale("D3:mixolydian")

The only thing i like about this one is that I created a bass line by taking it
down to D1.


[HYPERLINK](https://strudel.cc/?k0AX7srDMFIS)

[A question that arose to which I didn't know the answer to:
###how and where do we get samples from?]

i should start over for the beat because i'm using the percussion patch from last week
and only slighlty changing it. i feel bad for being lazy and want to see what else i can create.

this is my first attempt at trying to make a beat using linger:

new: https://strudel.cc/?_PYYfRgfohmv

it kind of sounds boring so I'm mixing it up with my glitchy patch.

[HYPERLINK](https://strudel.cc/?xBmvMzCb2ODB#CiQ6IG4ocmFuZC5yYW5nZSgwLDEyKS5zZWdtZW50KDgpKS5zY2FsZSgiRDI6bWl4b2x5ZGlhbiIpIC5zKCJzaW5lIikubWFzaygiPDEgWzAgMV0%2BIikucGFsaW5kcm9tZSgpLmdhaW4oNSkKCi8vYmFzcwokOiBuKHJhbmQucmFuZ2UoMCwxMikuc2VnbWVudCg5KSkuc2NhbGUoIkQwOmxvY3JpYW4iKSAucygic2luZSIpLmZhc3QoMikuZ2FpbigxMCkKCgovL2Nob3JkcwovLyQ6IG5vdGUgKCJbZDUsIGE1LCBhOV0gW35%2Bfn5dIFtjNiwgYTVdIikuZXVjbGlkKDYsOCkuZGVncmFkZUJ5KDAuMikKCi8vYmVhdAokOiBzdGFjayggCiAgIlt%2BIH4gfiB%2BIF0gW34gc24hMyxzbiE3IH4gfiBdIFt%2BIH4gfiB%2BIF0gW34gfiB%2BIH5dICIsIAogICJbfiB%2BIGJkITMwIH5dIFt%2BIH4gaGghMixoaCEzIH5dIFtoaCB%2BIGhoITE2MD8gfl0gIiwKICAiW34gfiB%2BIH5dIFtjcCB%2BIGNwIH5dIFt%2BIH4gY3Agfl0gW34gfiB%2BIGNwITNdICIsIAogICJbc24hMTAwPyB8IHNuITEwMCB8IGNwITIwMD8gXSBbfiB%2BIH4gfl0gIFtyaW0hMTIwPyBoaCEyMDA%2FXSAiLAopLnMoKS5nYWluKDAuMTApLmZhc3Qoc2luZSkubGluZ2VyKCI8MSAuNSAuMjA%2BIikKCiQ6IHMgKCJiZCoxMDAiKS5zdHJ1Y3QoInggfiB%2BIHggeCB4IH4geCIpLmxpbmdlcigiPDEgLjUgLjIwPiIpCiQ6IHMgKCJoaCozMCIpLnN0cnVjdCgifiB4IHggfiB%2BIH4geCB%2BIikuZmFzdCgyKS5saW5nZXIoIjwxIC41IC4yMD4iKQokOiBzICgicmltKjMwIikuc3RydWN0KCJ%2BIH4geCB%2BIH4gfiB4IH4iKS5saW5nZXIoIjwxIC41IC4yMD4iKQokOiBzICgiY3AqMzAiKS5zdHJ1Y3QoIn4gfiB%2BIH4gfiB%2BIH4gfiB%2BIH4geCB4IikubGluZ2VyKCI8MSAuNSAuMjA%2BIikKCgoKCgoKCgo%3D)


adding linger at the end because I want it to be in the grid so that it matches the other 3 lines wrote.

I think I like it better without the new lines I wrote so going back to my percussion
patch with a few changes, and using the linger function that we learned in last class.

After tweaking some things I finally made something that I think actually sounds okay:

[HYPERLINK](https://strudel.cc/?tRNc4ld8LpFC)

I stacked 2 line of code for the bass. they're both using they rand.range function,
but I put 8 segments and D0 mixolydian for one, and put 9 segments D locrian for the other one.
I wanted to create a busy and disorienting bass that didn't sound like a bass so I used
2 different modes, and to shake up the time feel changed one of the segments to 9. For the D mixolydian,
I used the mask function because I wanted to hear it stop every once in a while.

I like using fast(square) because it gives random pauses and it helps make the
patch more bareable and interesting when there is space.

And then I stacked three lines of code that use D minor with different registers.
That gave some cute melodic material to the patch. I like using fast(sine) here because
it adds nuanced phrasing by randomly stopping, instead of constantly looping the same thing.

The beat is very very simple. I wanted to slow it down a lot so it would sound
less generic.

Listening back, I thought it needed some distortion. I added gain(10) to the first
line.

Here is the finallll version:

[HYPERLINK](https://strudel.cc/?Plz3clodujv9)
