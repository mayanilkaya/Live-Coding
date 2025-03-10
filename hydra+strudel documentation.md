# Draft 1 for Strudel and Hydra patch

## learning Hydra

i went to youtube and searched hydra visuals and found codes for visuals that I liked to get some
inspiration.

[link for yt video](https://www.youtube.com/watch?v=Uj0a09VrK4M)

i'm looking at what was happening around 10:22.

i want to break down the the lines of codes here so I can understand the functions better and write my own.

### noise:

noise(scale, offset)

scale acts kind of like zoom in/out.
i looked at some documentations of javascript to understand better what the offset function is.
playing around with different values, and from what I've read : ".offset() returns an object containing the properties top and left."
i assume it has something to do with constantly (?) changing the starting point that
it creates a loop/motion effect. (not sure if that's correct)

I like this code I ended up with, using these 2 functions:

'javascript
await initHydra()
noise(300, 1).scale(10, 10, 0.1).out(o0)'

**I wish I knew a way to addd variations to this. ***come back here later!!!!***


### scale

scale(amount, xMult, yMult, offsetX, offsetY)

i replacecd the values of xmult with ymult and vice versa to be sure what
they meant. and the visual became vertical, when it was horizontal before.
they refer to values for x and y access.

this is just noise that looks like a static tv screen:

'javascript noise(300, 1).scale(0.1, 10, 0.1).out(o0)'

### osc

osc(frequency, sync, offset )

javascript 'osc(3, 0,[2.2, 1. , 3.5]).modulate(src(o0),1)'

this looks really cool just by itself without the noise function.
it seems like there's a color gradient that's shifting slowly but sharply. i believe
it's the values of the offset that are making that happen.

### modulate

modulate( texture, amount)

the higher of a number i put for texture, i get more lines. the amount kind of effects glitchy lines vs blocks of color.
**not so sure what amount does.**

*** one question that popped up in my head is where are these colors coming from? do i have a function
that;s defining the color grid that i'm not aware of? or is this the default? ***

*** also not sure if these 2 codes are working at the same time, or is my 2nd line of code
overriding the first one? *** nvm found out that it is. so for when i'm live coding i can comment out whatever line i want to.


I wanted to vary what I had so far, which is:

'javascript
noise(300, 1).scale(10, 10, 0.1).out(o0)
osc(3, 0,[2.2, 1. , 3.5]).modulate(src(o0),2).out(o0)
'
I waned to see if I could move the lines to horizontal. so i added a scale function :

'javascript
osc(3, 0,[2.2, 1. , 3.5]).modulate(src(o0),2).scale(0.1, 0.1, 0.1).out(o0)
'

[my code so far just so i don't lose it:](https://hydra.ojack.xyz/?code=bm9pc2UoMzAwJTJDJTIwMSkuc2NhbGUoMTAlMkMlMjAxMCUyQyUyMDAuMSkub3V0KG8wKSUwQSUwQW9zYygzJTJDJTIwMCUyQyU1QjIuMiUyQyUyMDEuJTIwJTJDJTIwMy41JTVEKS5tb2R1bGF0ZShzcmMobzApJTJDMikuc2NhbGUoMC4xJTJDJTIwMC4xJTJDJTIwMC4xKS5vdXQobzApJTBBJTBBJTJGJTJGb3NjKDMlMkMlMjAwJTJDJTVCMi4yJTJDJTIwMS4lMjAlMkMlMjAzLjUlNUQpLm1vZHVsYXRlKHNyYyhvMCklMkMyKS5vdXQobzApJTBBJTBBJTBBJTBBJTBB)

i like going back and forth between the version with scale and without scale.

'javascript osc(3, 0,[2.2, 1. , 3.5]).modulate(src(o0),1).scale(0.1, 0.1, 1, 10).out(o0)'
'javascript osc(3, 0,[2.2, 1. , 3.5]).modulate(src(o0),1).scale(5, 0.1, 1, 10).out(o0)'

I like these versions better because there's less movement so it's not so tiring.

adding another modulate function with noise and scale, and a render function.

i guess this is how we mix ? (render) 2 oscillator inputs:

'javascript
noise(300, 1).scale(10, 10, 0.1).out(o0)

osc(3, 0,[2.2, 1. , 3.5]).modulate(src(o0),1)

//osc(3, 0,[2.2, 1. , 3.5]).modulate(src(o0),1).scale(5, 0.1, 1, 10).out(o0)

.modulate(noise(3).scale(0.2, 110))

.out(o1)

render(o1)

'

i feel like only this information could be helpful for me to com eup with a 3-5 minute live
performance.

### experimenting with 4 inputs:

'javascript
noise(300, 1).scale(10, 10, 0.1).out(o0)

osc(3, 0,[2.2, 1. , 3.5]).modulate(src(o0),1)

//osc(3, 0,[2.2, 1. , 3.5]).modulate(src(o0),1).scale(0.5, 0.1, 1, 10).out(o0)

.modulate(noise(3).scale(0.2, 110))

.out(o1)

solid(1).out(o2)

gradient().out(o3)

render()
'

wanteed to add init cam but this is only for the left side of the scren. i want it on the right.

javascript'

noise(300, 1).scale(10, 10, 0.1).out(o0)

osc(3, 0,[2.2, 1. , 3.5]).modulate(src(o0),1)

//osc(3, 0,[2.2, 1. , 3.5]).modulate(src(o0),1).scale(0.5, 0.1, 1, 10).out(o0)

.modulate(noise(3).scale(0.2, 110))

.out(o1)

s3.initCam()
src(s3).color(-1, 1).out()

gradient().out(o3)

render()
'


some more variations:

'javascript
noise(300, 1).scale(10, 10, 0.1).out(o0)

osc(3, 0,[2.2, 1. , 3.5]).modulate(src(o0),2)

osc(3, 0,[2.2, 1. , 3.5]).modulate(src(o0),1).scale(1, 0.1, 1, 10).out(o0)

.modulate(noise(3).scale(0.2, 110)).out(o1)

gradient().out(o2)

solid(1).out(o3)


s3.initCam()
src(s3).color(-1, -1).out(o3)



render()

'
this stopped working idk why, going to the previous one to get it right.



I like this one:

'javascript
noise(300, 1).scale(10, 10, 0.1).out(o0)

//osc(3, 0,[2.2, 1. , 3.5]).modulate(src(o0),1)

osc(3, 0,[2.2, 1. , 3.5]).modulate(src(o1),1).scale(0.5, 0.1, 1, 10)

  .modulate(noise(3).scale(0.2, 110)).out(o0)


s2.initCam()
src(s2).color(-3, 1).out(o2)

s3.initCam()
src(s3).color(-1, -3).out(o3)



render()

'

I want to layer textures or lines on my face as well, or some things with motion.

i like this one yay:

'javascript
noise(300, 1).scale(10, 10, 0.1).out(o0)

//osc(3, 0,[2.2, 1. , 3.5]).modulate(src(o0),1)

osc(3, 0,[2.2, 1. , 3.5]).modulate(src(o1),1).scale(0.5, 0.1, 1, 10)

  .modulate(noise(3).scale(0.2, 110)).out(o0)


s2.initCam()
src(s2).color(-3, 1).out(o2)

s3.initCam()
src(s3).color(3, -1).layer(osc(0, 1, 0,1).color(0,0,0,()=>Math.sin(time*100))).out(o3)



render()
'

the colors match with each other.


want to go into my archive of videos to see if i'd like to import anything from there


#### another section of this video i like:

'javascript
noise(1)
.color(1,0,.2).shift(0.3)
.add(noise(2).rotate(2))

.add(noise(3).kaleid(99))

.mult(noise(20).thresh(.1))
.modulateScale(noise(.4).add(solid(1,1), -0.5),1)
.rotate(()=>time)
.blend(src(o0),.99)


.out(o)0'

understanding how to use the kaleid function i add some changes :

'javascript
noise(1)
.color(1,0,.2).shift(0.3)
.add(noise(2).rotate(2))

.add(noise(3).kaleid(99))

.mult(noise(20).thresh(.1))
.modulateScale(noise(.4).add(solid(1,1), -0.5),1)
.blend(src(o0),.99)
.out(o0)

osc(3, 0,[2.2, 1. , 3.5]).modulate(src(o0),1)

osc(3, 0,[2.2, 1. , 3.5]).modulate(src(o1),1).scale(0.5, 0.1, 1, 10)

  .modulate(noise(3).scale(0.2, 110)).out(o1)


s2.initCam()
src(s2).color(-3, -1).add(noise(3).kaleid(99)).out(o2)

s3.initCam()
src(s3).color(3, -1).layer(osc(0, 1, 0,1).color(0,0,0,()=>Math.sin(time*100))).out(o3)



render()'

### other variations:

'javascript
noise(20)
.color(1,0,.2).shift(0.3)
.add(noise(2).rotate(2))
  .add(noise(3).kaleid(99))
.mult(noise(20).thresh(1).brightness(1))
.modulateScale(noise(1).add(solid(1,1), -0.5),1)
.blend(src(o0),.99)

.out(o0)

osc(3, 0,[2.2, 1. , 3.5]).modulate(src(o0),1)

osc(3, 0,[2.2, 1. , 3.5]).modulate(src(o1),1).scale(0.5, 0.1, 1, 10)

  .modulate(noise(3).scale(0.2, 110)).out(o1)


s2.initCam()
src(s2).color(-3, -1).add(noise(3).kaleid(99,()=>Math.sin(time*6))).out(o2)

s3.initCam()
src(s3).color(3, -1).layer(osc(0, 1, 0,1).color(0,0,0,()=>Math.sin(time*100))).out(o3)



render()'


i found out about the glitch library p5. i want to use that with webcam:

[I did it with this code by looking at the documentation here:](https://hydra.ojack.xyz/?code=YXdhaXQlMjBsb2FkU2NyaXB0KCUyMmh0dHBzJTNBJTJGJTJGY2RuLmpzZGVsaXZyLm5ldCUyRm5wbSUyRnA1LmdsaXRjaCU0MGxhdGVzdCUyRnA1LmdsaXRjaC5qcyUyMiklMjAlMkYlMkZsb2FkcyUyMHA1Z2xpdGNoJTIwbGlicmFyeSUyMGluJTIwSHlkcmElMEElMEElMkYlMkZnZW5lcmF0ZSUyMGElMjB2YXJpYWJsZSUyMGZvciUyMGdsaXRjaCUyMCUwQWxldCUyMGdsaXRjaCUzQiUwQSUwQXAlMjAlM0QlMjBuZXclMjBQNSgpJTIwJTJGJTJGbG9hZCUyMHA1JTIwaW4lMjBIeWRyYSUwQWdsaXRjaCUyMCUzRCUyMG5ldyUyMEdsaXRjaChwKSUzQiUyMCUyRiUyRmxvYWRzJTIwZ2xpdGNoJTIwbGliLiUyMEl0J3MlMjBpbXBvcnRhbnQlMjB0byUyMGxpbmslMjBwNSdzJTIwdmFyaWFibGUlMjBoZXJlJTIwKHApLiUwQSUyRiUyRmxvYWQlMjBhbnklMjBVUkwncyUyMGltYWdlJTIwaGVyZSUwQXAubG9hZEltYWdlKCdodHRwcyUzQSUyRiUyRnVwbG9hZC53aWtpbWVkaWEub3JnJTJGd2lraXBlZGlhJTJGY29tbW9ucyUyRjElMkYxYiUyRlRyaWFuZ3Vsb19IU1YucG5nJyUyQyUyMGZ1bmN0aW9uKGltKSUyMCU3QiUwQWdsaXRjaC5sb2FkSW1hZ2UoaW0pJTNCJTBBJTdEKSUzQiUwQSUwQSUyRiUyRnRoaXMlMjBzaG91bGQlMjBiZSUyMGxvYWQlMjBiZWZvcmUlMjBwNSdzJTIwZHJhdyUyMGZ1bmN0aW9uJTBBZ2xpdGNoLmxvYWRUeXBlKCdqcGcnKSUzQiUyMCUyRiUyRmRlZmluZSUyMHR5cGUlMjBvZiUyMGdsaXRjaCUyMGZpbGUlMEFnbGl0Y2gubG9hZFF1YWxpdHkoMC4xKSUzQiUyMCUyRiUyRmRlZmluZSUyMGdsaXRjaCUyMHF1YWxpdHklMkMlMjB0aGUlMjBsZXNzJTIwcXVhbGl0eSUyQyUyMG1vcmUlMjBnbGl0Y2hlcyUwQXAuaW1hZ2VNb2RlKHAuQ0VOVEVSKSUzQiUwQSUwQXAuZHJhdyUyMCUzRCUyMCgpJTIwJTNEJTNFJTIwJTdCJTBBJTA5cC5jbGVhcigpJTNCJTBBJTA5Z2xpdGNoLnJlc2V0Qnl0ZXMoKSUzQiUyMCUwQSUwOWdsaXRjaC5yZXBsYWNlQnl0ZXMoMTAwJTJDJTIwMTA0KSUzQiUyMCUwQSUwOWdsaXRjaC5yYW5kb21CeXRlcygxMDApJTNCJTBBJTA5Z2xpdGNoLmxpbWl0Qnl0ZXMoMC4xKSUzQiUwQSUwOWdsaXRjaC5idWlsZEltYWdlKCklM0IlMEElMDlwLmltYWdlKGdsaXRjaC5pbWFnZSUyQyUyMHAud2lkdGglMkYyJTJDcC5oZWlnaHQlMkYyKSUwQSU3RCUwQSUyRiUyRmhpZGUlMjBwNSdzJTIwY2FudmFzJTBBcC5oaWRlKCklM0IlMEElMEElMkYlMkZsb2FkJTIwcDUlMjBzb3VyY2UlMjB0byUyMHVzZSUyMGl0JTIwaW4lMjBIeWRyYSUwQXMwLmluaXQoJTdCc3JjJTNBJTIwcC5jYW52YXMlN0QpJTIwJTBBJTBBb3NjKDEwKS5sYXllcihzcmMoczApLm1vZHVsYXRlKG5vaXNlKDIpKSkub3V0KCk=)

I just found a spot to initialize the webcam as a source and it worked. i don't like the effects though, so i'll change that. lol it looks like im underwater.

i don't understand why i'm floating in the background:

'javascript
await loadScript("https://cdn.jsdelivr.net/npm/p5.glitch@latest/p5.glitch.js") //loads p5glitch library in Hydra

//generate a variable for glitch
let glitch;

p = new P5() //load p5 in Hydra
glitch = new Glitch(p); //loads glitch lib. It's important to link p5's variable here (p).
//load any URL's image here
s0.initCam() //initialize webcam as external source 's0'
src(s0).out() // use external source 's0' inside Hydra
p.initCam
glitch.initCam;
;

//this should be load before p5's draw function
glitch.loadType('jpg'); //define type of glitch file
glitch.loadQuality(0.1); //define glitch quality, the less quality, more glitches
p.imageMode(p.CENTER);

p.draw = () => {
	p.clear();
  glitch.pixelate(0.1);
	glitch.resetBytes();
glitch.randomByte(12); // the 123rd byte
glitch.randomByte('7b'); // the 123rd byte, using hex
	glitch.randomBytes(100);
	glitch.limitBytes(0.1);
	glitch.buildImage();
	p.image(glitch.image, p.width/2,p.height/2)
}
//hide p5's canvas
//p.hide();

//load p5 source to use it in Hydra
s0.init({src: p.canvas})

noise(1).layer(src(s0).modulate(noise(2))).out()'

omg meanwhile i found this one and it's sick:

'javascript
osc(18, 0.1, 0).color(2, 0.1, 2)
.mult(osc(20, 0.01, 0)).repeat(2, 20).rotate(0.5).modulate(o1)
.scale(1, () =>  (a.fft[0]*0.9 + 2)).diff(o1).out(o0)
osc(20, 0.2, 0).color(2, 0.7, 0.1).mult(osc(40)).modulateRotate(o0, 0.2)
.rotate(0.2).out(o1)'


****

i can't find the correct hydra patch that i did. when i copy paste what
i have in the documentation file im getting errors.

[here is the correct link:](https://hydra.ojack.xyz/?sketch_id=VTt5GAmoQuTsmYjQ)

[my strudel patch](https://strudel.cc/?twYHkomtPJ3w)

[new strudel patch with ag cook inspiration](https://strudel.cc/?iPqriFqbxOET)

i need drums and bass?



'javascript
await initHydra()

noise(20)
.color(1,0,.2).shift(0.3)
.add(noise(2).rotate(2))
  .add(noise(3).kaleid(99))
.mult(noise(20).thresh(1).brightness())
.modulateScale(noise(1).add(solid(1,1), -0.5),1)
.blend(src(o0),.99)

.out(o0)

osc(3, 0,[2.2, 1. , 3.5]).modulate(src(o0),1)

osc(3, 0,[2.2, 1. , 3.5]).modulate(src(o1),1).scale(0.5, 0.1, 1, 10)

  .modulate(noise(3).scale(0.2, 110)).out(o1)


s2.initCam()
src(s2).color(-3, -1).add(noise(3).kaleid(99)).out(o2)

s3.initCam()
src(s3).color(3, -1).layer(osc(0, 1, 0,1).color(0,0,0,()=>Math.sin(time*100))).out(o3)



render()


$: sound("brown")._scope().delay(1)
$: s("crackle*4").density("<0.01 0.04 0.2 0.5>".slow(2))._scope().crush("<16 8 7>")
$: note("c#4, e4, d#4").struct("x ~ ~ ~").lpf("<1000 500>").slow(5).phaser("<1 8>")

$: note("g#4, g#5") .struct("<~ ~ x ~ ~ ~ ~ ~ >").lpf("<1000 500>").crush("16")

$: note("e4, a4, c#4") .struct("< x x ~ ~ >").lpf(500).delay("<0.5 1>")

$: note("d#4, a4, c#4") .struct("< ~ ~ x ~ >").lpf(500).delay("1").room(".8").size("4").phaser("<8 1>")


$: note("e6 e6 c#5 [a5,d#5]").mask("<1 [0 1]>").lpf("<500 1000>").delay("<0 .25 .5 1>").pan("<.5 1 .5 0>")

$: n(rand.range(0,12).segment(6)) .scale("a3:lydian") .s("gm_guitar_harmonics").jux(iter(4)).phaser("<8 1>").room("1").pan("<.5 1 .5 0>")

$: n(rand.range(0,12).segment(6)) .scale("a5:lydian") .s("gm_whistle").jux(iter(4)).phaser("<8 1>").distort(.1).room("1").gain(1)
$: n(rand.range(0,12).segment(6)) .scale("a4:lydian") .s("gm_guitar_harmonics").delay("<.5 1>").distort(3).gain(.1)


'


*audio reactivity with hydra*
const mymelody = "c d e g";

put this at the top and then put something in your music to sync it with bpm.


[NEW UPDATES ON PATCH]https://strudel.cc/?DY_ytEp6JSM3

#### final
###### i guess i'm trying to create a beat?

I want a glitchy minimal microbeat.

I added this as maybe bass or just for some low frequency rumbling:

'javascript
s: s(("sine").gain("1")).segment(12)
.lpf("2000")'

going to go back and forth between fast(5) and fast(2).
5 is more rumbly and 2 is more like a bass
1.5 for gain and 8 for postgain seems like a good balance for now.

***hihats***

'javascript
$: s("white!32?").gain(0.5).decay(.1)'

learned the white noise trick for hihats in class
when we had the strudel developer visit.

decay is .1 because I want it to be a short sound.

actualy !16? is better, 32 was too busy.

I had .mul(0.015) in this code, but can't tell the difference without it so i'm getting rid of it.
i also had fast(5) but it sounds better at its normal speed so getting rid of that too.

I want to add a phaser sweep so it's more dynamic.
I added a phasersweep, and delayfeedback.
the delayfeedback is changing between paraemetrs so I made the delay change too, to create even more of a dynamic contrast.

to have a little bit of a groove,

I've added

$: sound("bd*2,<white pink brown>*8")
.decay(.04).sustain(0)

i'm randomizing it with fats(sine)so that we don't have the same beat and so that it's fun.
added some distortion but i'm having trouble gainstaging.
distort("2:0.5") and .postgain(0.5) seems to work for now.

going back to bass, i deleted distortion. postgain at 4 is the perfect mix with the chords.

I've layered all of my chords, the bass and the beat and the beat sounds too loud. even when i adjust the gain/postgain parameters.

*it's because i had 0.9 in for gain where it should've been 0.1 for quieter. also i changed its place with fast(sine), so maybe bringing it up forward helped too*

i like the feel of it but i don't like how dry it sounds.
coarse makes it more interesting.

added decay(0.1) and prelease(0.1)
 to get a shorter release. i repeated decay twice,
and i'm not sure what that means but there is a difference when i do it and don't do it.
i like the sound beter with it repated.
 i wanted to change the timbre a little bit but im not sure how.


added attack and degrade by. i can change the fastnesss from sine to 10 to get a fast beat, and degrade it and add the attacks to add variations.

moving on to the hihat:

i dont like how long the release and decay is even thoguh
when i put in values that would have it shorter.
I changed decay to 0 (you have to have sustain lower than 1 for decay to work), and white noise turned into a click. i like this more for microbeat .

I copied what i did for the whie noise for a g0 sine wave. i wanted to double it to get a fuller sound.

i created this kick:
$: note ("g0!16?").sound("sine").gain(10)
  .coarse("<2 4 6 8>*4")
.postgain(.8)
.lpf("<500 700>")

but when i paste it on my actual patch it sounds really distorted and not what its suppposed o be like. i just have to be careful of the gain levels.

okay after adjusting the gains, i have the micro beat i want. i can just change the parameters i want when performing to create variations i like.

*taking the ambient section in and out is important to hear the beat.*

sounds better without the low frequencies droning( i was trying to create a weird bass)

[here is my strudel patch so far](https://strudel.cc/?nh7ZqiyT7Q2L)

i don't like my melodies:

i added the const slider. i'm not exactly sure what i want the melodies to sound like.
i don't really want to have a specific melody i guess.

[with the slider](https://strudel.cc/?0onI6612zoDX)

I realized I didn't really want to have a melody, so to create a new section I changed the key to C from A lydian. I've created a section with pads and using the seed, ribbon and degradeby function to have pitches enter for a really short amount of time and leave. there wasn't really much troubleshooting or debugging going on other than trying to create a composition i liked.

[hopefully final version](https://strudel.cc/?6jMt7EZZYCZB)

### adding my HYDRA PATCH

[link for hydra](https://hydra.ojack.xyz/?code=JTJGJTJGJTIwbGljZW5zZWQlMjB3aXRoJTIwQ0MlMjBCWS1OQy1TQSUyMDQuMCUyMGh0dHBzJTNBJTJGJTJGY3JlYXRpdmVjb21tb25zLm9yZyUyRmxpY2Vuc2VzJTJGYnktbmMtc2ElMkY0LjAlMkYlMEFub2lzZSgyMCklMEEuY29sb3IoMSUyQzAlMkMuMikuc2hpZnQoMC4zKSUwQS5hZGQobm9pc2UoMikucm90YXRlKDIpKSUwQSUyMCUyMC5hZGQobm9pc2UoMykua2FsZWlkKDk5KSklMEEubXVsdChub2lzZSgyMCkudGhyZXNoKDEpLmJyaWdodG5lc3MoMSkpJTBBLm1vZHVsYXRlU2NhbGUobm9pc2UoMSkuYWRkKHNvbGlkKDElMkMxKSUyQyUyMC0wLjUpJTJDMSklMEEuYmxlbmQoc3JjKG8wKSUyQy45OSklMEElMEEub3V0KG8wKSUwQSUwQW9zYygzJTJDJTIwMCUyQyU1QjIuMiUyQyUyMDEuJTIwJTJDJTIwMy41JTVEKS5tb2R1bGF0ZShzcmMobzApJTJDMSklMEElMEFvc2MoMyUyQyUyMDAlMkMlNUIyLjIlMkMlMjAxLiUyMCUyQyUyMDMuNSU1RCkubW9kdWxhdGUoc3JjKG8xKSUyQzEpLnNjYWxlKDAuNSUyQyUyMDAuMSUyQyUyMDElMkMlMjAxMCklMEElMEElMjAlMjAubW9kdWxhdGUobm9pc2UoMykuc2NhbGUoMC4yJTJDJTIwMTEwKSkub3V0KG8xKSUwQSUwQSUwQXMyLmluaXRDYW0oKSUwQXNyYyhzMikuY29sb3IoLTMlMkMlMjAtMSkuYWRkKG5vaXNlKDMpLmthbGVpZCg5OSUyQygpJTNEJTNFTWF0aC5zaW4odGltZSo2KSkpLm91dChvMiklMEElMEFzMy5pbml0Q2FtKCklMEFzcmMoczMpLmNvbG9yKDMlMkMlMjAtMSkuYWRkKG5vaXNlKDkpLmNvbG9yKDAlMkMxJTJDLTMlMkMoKSUzRCUzRU1hdGguc2luKHRpbWUqMSkpKS5vdXQobzMpJTBBJTBBJTBBJTBBcmVuZGVyKCklMEE%3D)

i wanted to sink it to my music. the strudel documentation might be hekpful.


[hydra + strudel without audioreactivity](https://strudel.cc/?FflxR_s3-_iW)
