# Art that uses Computers and Software

### On the name

What we will be talking about today is the use of computers and software to
help generate, or generate in its entirety, something that may be called "art".
There are many terms and names that can be used to describe this, an a few are
mentioned below.

* generative art - can include non-computerized art as well
* computer art - can be too vague, as using photoshop could fall into this
  category
* digital art - same problem as computer art
* algorithmic art - focuses on the computer algorithms
* procedural generation - the world "procedural generation" is usually used in the
  context of video games, not usually "Art" - with a capital A
* and more, I'm sure.

Note that all of these terms have their own *seperate* wikipedia entry, in that
they are all distinct.

### Some areas we will try to discuss

1. Fractals
1. Procedural content in games
1. Music
1. Source Code as Art
1. Neural Network Algorithms

### Fractals

* One of the first widely popular uses for algorithms to create really cool
  artwork
* There is an intense amount of math that is used to describing fractals
	* Z = Z^2 + C is the formula for the *mandelbrot* fractal
	* contains infinite detail, and repeating "self-similar" structures, has a
	  "fractal dimension"
	* *many* applications, and real world examples
* many different ways to *interpret* the formula as an image:
	1. ![standard](http://www.eddaardvark.co.uk/python_patterns/images/w21.gif)
	3. ![star](http://www.eddaardvark.co.uk/python_patterns/images/w21s.gif)
	2. ![quadrant](http://www.eddaardvark.co.uk/python_patterns/images/Q013.png)
	5. ![?](http://www.eddaardvark.co.uk/python_patterns/images/w21b.gif)
	6. ![bands](http://www.eddaardvark.co.uk/python_patterns/images/b2.gif)
		* "In this scheme you keep iterating z until you reach a point (x+iy)
		  that has a modulus greater than 2 (x2 + y2 >  4). You then calculate
		  the arc tangent of y ∕ x and use that as an index into the colour
		  map. The result is an image like the one on the left." [source
		  ](http://www.eddaardvark.co.uk/python_patterns/schemes.html)
* Electric Sheep screensaver - distributed rendering and genetic selection
  algorithm for parameterized [flame fractal](https://en.wikipedia.org/wiki/Fractal_flame)
	* [](http://lmgtfy.com/?s=d&q=electric+sheep)
	* ![sheep1](https://upload.wikimedia.org/wikipedia/commons/5/52/Electricsheep-3404.jpg)
	* ![sheep2](http://2.bp.blogspot.com/-CnCvKI2VoiQ/VQm_Qy8CriI/AAAAAAAAMOk/AeHiBvcsd_w/s1600/1290610562-screen-shot-2010-11-24-at-113758-am-528x391.png)

### Procedural content in games

* MANY examples of using computers to *generate* content, rather than having
  artists *create* content
	* no mans sky - attempt at a procedurally generated universe
	* diablo - randomly generated items, levels, enemies
	* minecraft - randomly generated world
* Creating terrain, maps/levels, items, artwork, backgrounds,
* Some basic algorithms such as noise generation can make things like clouds,
  or mountain ranges
* ex) L-Systems - generative grammar
* demos! From artist Inigo Quilez
	1. Elevated Demo: [https://www.youtube.com/watch?v=r_6aTdscdZw&list=PL0EpikNmjs2Dz45-Ru7Rfp8zQ48fI5QOa&index=1]
	1. Mathematically defined scenes: [https://www.youtube.com/watch?v=__G43hELHL0&list=PL0EpikNmjs2Dz45-Ru7Rfp8zQ48fI5QOa&index=5]

### Music

* Using computers to generate new music, with or without any human intervening!
* ex) Markov Chains
	* analyse music and record statistical composition of notes
	* For instance, find the probability of the note A# following the note C
	* After all the probabilities are recorded, randomly sample a note, given
	  the probability distribution calculated earlier
	* So, if the last note was a C, there will be some probability that the
	  next letter will be an A#
	* can form larger probability distributions by thinking about more than the
	  last letter (for instance, given the last two, three, or four notes, etc)
	  but requires much more time and input to generate a good distribution
	* We can also use a NN to generate and sample in a similar manner using
	  LSTM networks
* Genetic algorithms, Generative Grammar systems (such as L-systems), Fractals,
  Artifical Intelligence, etc. can/are utilized
* For more, here's a cool summary paper: [http://peterlangston.com/Papers/amc.pdf]
  that describes in more detail 6 different methods in the literature.
* Quick note on factals, as described in the paper:
  Used to interpolate between notes based on a random brownian motion fractal

### Source Code Poetry

```
You will(Need no){
	Example at=ALL;
	if (You.are(GOOD))
		at.writing(Your.CODE);
}
```

* Famous Perl program [Black Perl](https://en.wikipedia.org/wiki/Black_Perl)
* Ongoing competition at [http://sourcecodepoetry.com/]
* Aside from poetry, things like code golf, quines, and esolangs can be seen as
  art forms

```perl
BEFOREHAND: close door, each window & exit; wait until time.
    open spellbook, study, read (scan, select, tell us);
write it, print the hex while each watches,
    reverse its length, write again;
    kill spiders, pop them, chop, split, kill them.
        unlink arms, shift, wait & listen (listening, wait),
sort the flock (then, warn the "goats" & kill the "sheep");
    kill them, dump qualms, shift moralities,
    values aside, each one;
        die sheep! die to reverse the system
        you accept (reject, respect);
next step,
    kill the next sacrifice, each sacrifice,
    wait, redo ritual until "all the spirits are pleased";
    do it ("as they say").
do it(*everyone***must***participate***in***forbidden**s*e*x*).
return last victim; package body;
    exit crypt (time, times & "half a time") & close it,
    select (quickly) & warn your next victim;
AFTERWARDS: tell nobody.
    wait, wait until time;
    wait until next year, next decade;
        sleep, sleep, die yourself,
        die at last
# Larry Wall
```

### Artifical Intelligence / Neural Networks

* Using advances in AI, we can make really cool art!

* Neural networks for artistic styling
	* ![nnstyle1](https://raw.githubusercontent.com/jcjohnson/neural-style/master/examples/outputs/golden_gate_seated.png)
	* [many more examples](https://github.com/jcjohnson/neural-style)
	* Or, see the actuall research paper! [http://arxiv.org/abs/1508.06576]
	* How does it work:
		* different layers (or groups of neurons) learn different bits of
		  information - for instance, some are more suceptible to color, while
		  others pick up sharp edges
		* These neurons build more and more abstract/conceptual "features"
		* By taking
	* Has also been used to make short videos
		* [https://www.youtube.com/watch?v=Khuj4ASldmU]
* Google "Inceptionism"
	* uses googles inception Neural Network archetecture
	* the goal was to find out what image classifying neural nets were actually
	  seeing and using to identify images
	* The idea was, rather than feed an image of a banana as an ilput, and adjust the
	  **network** to better identify bananas, feed the **network** as the input,
	  and adjust the **image** to be a better banana.
	* It didn't work so well at first - created very unrealistic images
		* for instance, horizontal yellow and black lines is what the network
		  say as a schoolbus
	* added the constraint that the image "look real" (by following
	  statistical norms of real images - don't ask me the specifics)
	* ![banana](https://4.bp.blogspot.com/-tTYZpdJ18bg/VYITAO4s_uI/AAAAAAAAAlE/L7VMImFFt_M/s640/noise-to-banana.png)
	* ![assorted images](https://2.bp.blogspot.com/-17ajatawCW4/VYITTA1NkDI/AAAAAAAAAlM/eZmy5_Uu9TQ/s640/classvis.png)
	* ![clouds](https://4.bp.blogspot.com/-FPDgxlc-WPU/VYIV1bK50HI/AAAAAAAAAlw/YIwOPjoulcs/s640/skyarrow.png)
	* ![clouds-zoom](https://3.bp.blogspot.com/-R15_fyB-ZpE/VYIV-Uu9iwI/AAAAAAAAAl4/o3heQNGpVRU/s640/Funny-Animals.png)
	* ![stuff](https://2.bp.blogspot.com/-nxPKPYA8otk/VYIWRcpjZfI/AAAAAAAAAmE/8dSuxLnSNQ4/s640/image-dream-map.png)
	* ![assorted cool images](https://1.bp.blogspot.com/-XZ0i0zXOhQk/VYIXdyIL9kI/AAAAAAAAAmQ/UbA6j41w28o/s640/building-dreams.png)
* Generative Adversarial Networks
	* uses two "battling" networks to generate 'realistic' images
	* one network learns to generate images, based on an input of actual images
	* another network learns to discriminate between 'real' and 'fake'/'generated' images.
	* The output of the generative network is used to train the discriminator, while the discriminator is used to train the generator

	# Thanks for Listening!

[https://www.youtube.com/watch?v=XhdACpKBUcs&list=PL0EpikNmjs2Dz45-Ru7Rfp8zQ48fI5QOa&index=14]

* Some Cool Stuff:
	* from doodle to art![https://www.youtube.com/watch?v=jMZqxfTls-0]
	* using AI to
