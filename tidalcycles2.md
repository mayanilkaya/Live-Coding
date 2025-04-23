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

### palindrome makes it goes forward and backwards:

d1 $ sometimes (palindrome) $ n "0 1 [~ 2] 3" # sound "arpy"

linger and degrade -- strudel

### chunk'

d5 $ chunk' 3 (hurry 2) $ n ("7 2 [3 2] ~") # s "lith"

### pentatonic and hexatonic scales ( picking out 5-6 notes) with a touch of randomness with the operator |+ irand 11
11 is however many things there are in the sample pack

the sample array is print

d5 $ n ("1 ~ 2 [3 2] ~" |+ irand 11) # s "print"

### recording:

in supercollider

s.record; (in stereo by default)
s.stopRecording;
s.meter;

if you want to do  multichannel-- s.record(numChannels:4);

### loading your own samples

(
s.options.numBuffers = 1024 * 256;
s.options.memSize = 8192 * 32;
s.options.maxNodes = 1024 * 32;sx
s.options.numOutputBusChannels = 2; // total number of output channels
s.options.numInputBusChannels = 2;

s.waitForBoot {
    ~dirt = SuperDirt(2, s); // total number of output channels
	~dirt.loadSoundFiles;
    ~dirt.loadSoundFiles("/Users/rrome/Documents/GitHub/mehetabel/Dirt/samples/**"); // specify sample folder to load THIS IS THE RACHEL PATH
    s.sync; // wait for supercollider to finish booting up
    ~dirt.start(57120, 0 ! 12); // start superdirt, listening on port 57120, create twelve orbits each sending audio to channel 0
};
);

file structure: in a folder called Dirt, have a folder called samples. put your samples
within that folder and create a new folder for every sample and name it after the samples
everything has to be numbered: samples-donna-00_donna.wav and 01_donna.wav

* they have to be wav files
