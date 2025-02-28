# 04 intro to Hydra

source -- bus name

stacks for visuals
4 buses and output them in 4 ways

https://hydra.ojack.xyz/garden/

https://github.com/zachkrall/hydra-examples

'javascript
// licensed with CC BY-NC-SA 4.0 https://creativecommons.org/licenses/by-nc-sa/4.0/
// by Rodrigo Velasco
// https://yecto.github.io/

osc(18, 0.1, 0).color(2, 0.1, 2)
.mult(osc(20, 0.01, 0)).repeat(2, 20).rotate(0.5).modulate(o1)
.scale(1, () =>  (a.fft[0]*0.9 + 2)).diff(o1).out(o0)
osc(20, 0.2, 0).color(2, 0.7, 0.1).mult(osc(40)).modulateRotate(o0, 0.2)
.rotate(0.2).out(o1)
'


'javascript
osc(5,.1).modulate(noise(6),.22).diff(o0)
  	.modulateScrollY(osc(2).modulate(osc().rotate(),.11))
	.scale(.72).color(0.99,1.014,1)
  	.out()
'

https://hydra.ojack.xyz/?sketch_id=oDfCUlAvtiNCCvZq

you can run the code in the javascript console if you wanted to hide your code

complete rough draft for next week
strudel guest next week
3-5 min live performance using strudel and hydra in 2 weeks
