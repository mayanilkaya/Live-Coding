# Draft 1 for Strudel and Hydra patch

## learning Hydra

i went to youtube and searched hydra visuals and found codes for visuals that I liked to get some
inspiration.

[HYPERLINK](https://www.youtube.com/watch?v=Uj0a09VrK4M)

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
my code so far just so i don't lose it:
[HYPERLINK](https://hydra.ojack.xyz/?code=bm9pc2UoMzAwJTJDJTIwMSkuc2NhbGUoMTAlMkMlMjAxMCUyQyUyMDAuMSkub3V0KG8wKSUwQSUwQW9zYygzJTJDJTIwMCUyQyU1QjIuMiUyQyUyMDEuJTIwJTJDJTIwMy41JTVEKS5tb2R1bGF0ZShzcmMobzApJTJDMikuc2NhbGUoMC4xJTJDJTIwMC4xJTJDJTIwMC4xKS5vdXQobzApJTBBJTBBJTJGJTJGb3NjKDMlMkMlMjAwJTJDJTVCMi4yJTJDJTIwMS4lMjAlMkMlMjAzLjUlNUQpLm1vZHVsYXRlKHNyYyhvMCklMkMyKS5vdXQobzApJTBBJTBBJTBBJTBBJTBB)

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

I did it with this code by looking at the documentation here: [HYPERLINK](https://hydra.ojack.xyz/?code=YXdhaXQlMjBsb2FkU2NyaXB0KCUyMmh0dHBzJTNBJTJGJTJGY2RuLmpzZGVsaXZyLm5ldCUyRm5wbSUyRnA1LmdsaXRjaCU0MGxhdGVzdCUyRnA1LmdsaXRjaC5qcyUyMiklMjAlMkYlMkZsb2FkcyUyMHA1Z2xpdGNoJTIwbGlicmFyeSUyMGluJTIwSHlkcmElMEElMEElMkYlMkZnZW5lcmF0ZSUyMGElMjB2YXJpYWJsZSUyMGZvciUyMGdsaXRjaCUyMCUwQWxldCUyMGdsaXRjaCUzQiUwQSUwQXAlMjAlM0QlMjBuZXclMjBQNSgpJTIwJTJGJTJGbG9hZCUyMHA1JTIwaW4lMjBIeWRyYSUwQWdsaXRjaCUyMCUzRCUyMG5ldyUyMEdsaXRjaChwKSUzQiUyMCUyRiUyRmxvYWRzJTIwZ2xpdGNoJTIwbGliLiUyMEl0J3MlMjBpbXBvcnRhbnQlMjB0byUyMGxpbmslMjBwNSdzJTIwdmFyaWFibGUlMjBoZXJlJTIwKHApLiUwQSUyRiUyRmxvYWQlMjBhbnklMjBVUkwncyUyMGltYWdlJTIwaGVyZSUwQXAubG9hZEltYWdlKCdodHRwcyUzQSUyRiUyRnVwbG9hZC53aWtpbWVkaWEub3JnJTJGd2lraXBlZGlhJTJGY29tbW9ucyUyRjElMkYxYiUyRlRyaWFuZ3Vsb19IU1YucG5nJyUyQyUyMGZ1bmN0aW9uKGltKSUyMCU3QiUwQWdsaXRjaC5sb2FkSW1hZ2UoaW0pJTNCJTBBJTdEKSUzQiUwQSUwQSUyRiUyRnRoaXMlMjBzaG91bGQlMjBiZSUyMGxvYWQlMjBiZWZvcmUlMjBwNSdzJTIwZHJhdyUyMGZ1bmN0aW9uJTBBZ2xpdGNoLmxvYWRUeXBlKCdqcGcnKSUzQiUyMCUyRiUyRmRlZmluZSUyMHR5cGUlMjBvZiUyMGdsaXRjaCUyMGZpbGUlMEFnbGl0Y2gubG9hZFF1YWxpdHkoMC4xKSUzQiUyMCUyRiUyRmRlZmluZSUyMGdsaXRjaCUyMHF1YWxpdHklMkMlMjB0aGUlMjBsZXNzJTIwcXVhbGl0eSUyQyUyMG1vcmUlMjBnbGl0Y2hlcyUwQXAuaW1hZ2VNb2RlKHAuQ0VOVEVSKSUzQiUwQSUwQXAuZHJhdyUyMCUzRCUyMCgpJTIwJTNEJTNFJTIwJTdCJTBBJTA5cC5jbGVhcigpJTNCJTBBJTA5Z2xpdGNoLnJlc2V0Qnl0ZXMoKSUzQiUyMCUwQSUwOWdsaXRjaC5yZXBsYWNlQnl0ZXMoMTAwJTJDJTIwMTA0KSUzQiUyMCUwQSUwOWdsaXRjaC5yYW5kb21CeXRlcygxMDApJTNCJTBBJTA5Z2xpdGNoLmxpbWl0Qnl0ZXMoMC4xKSUzQiUwQSUwOWdsaXRjaC5idWlsZEltYWdlKCklM0IlMEElMDlwLmltYWdlKGdsaXRjaC5pbWFnZSUyQyUyMHAud2lkdGglMkYyJTJDcC5oZWlnaHQlMkYyKSUwQSU3RCUwQSUyRiUyRmhpZGUlMjBwNSdzJTIwY2FudmFzJTBBcC5oaWRlKCklM0IlMEElMEElMkYlMkZsb2FkJTIwcDUlMjBzb3VyY2UlMjB0byUyMHVzZSUyMGl0JTIwaW4lMjBIeWRyYSUwQXMwLmluaXQoJTdCc3JjJTNBJTIwcC5jYW52YXMlN0QpJTIwJTBBJTBBb3NjKDEwKS5sYXllcihzcmMoczApLm1vZHVsYXRlKG5vaXNlKDIpKSkub3V0KCk=)

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
