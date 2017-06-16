---
layout: post
title: interferometry
comments: true
permalink: /:title
image: ''
date:   2017-06-16 00:23:50
tags:
- Astronomy
description: 'Interferometry Notes'
categories:
- Astronomy, Science
serie: learn


---
# Interferometry

Hello guys, this post is kind of notes for me. As I am not much into astronomy, I will try to cover the very basics of it. It is purely scientific and theoretical and don't require any astronomical prerequisite.

### What is Interferometry?

Well, Interferometry is the practice of using a two or more element radio telescope array to observe astronomical, sources this array itself along with the electronics used to synthesize the signals is what we call the *Interferometer*. But first what I have an Interferometer at all. Well, for a single telescope, Its resolution can be approximated as 

​								$R=\frac{\lambda}{D}$

Where, $\lambda$ is the wavelength of the source we're trying to observe over the diameter, $D$  of the telescope. So, this means that for any given wavelength if we want better resolution, we need to build telescope with larger and larger diameter, but building large diameter telescope is difficult and expensive. Its lucky for us, it turns out that for an array of telescopes like an interferometer, this resolution equation modifies to 

​								$R=\frac{\lambda}{B}$

Where, B is the largest separation between any two telescope and the separation acts as the effective diameter of the array, so along with being more cost-effective and practical to build an array of telescopes also gives a separate control over the collecting area and resolution of a telescope. Here is how an interferometer looks like.

![](http://www.cv.nrao.edu/course/astr534/images/WSRT.jpg)



First we have two antennas, lets call it $i​$ and $j​$  and these two antennas are separated by certain distance which we call the *baseline*, $B​$. They both point towards a $$source_1​$$ in the sky in the the direction of the unit vector $\vec{s_1}​$ . They will both receive a signal from this source. However, because the antennas are separated by the distance $B​$, they won't receive the signal in the same time because  the astronomical sources are far away the signals received by the telescopes are plane waves. so we are  going  to have a plane wavefront coming through the sky and hitting the telescopes. We can see from the figure that one of the antennas, i.e Antenna $i​$ is just a tad bit closer to the source and the other end. It is this antenna $i​$ which will receive the signals first so, the time difference in which the second antenna $j​$ receives the same wave as first. We call the time difference as the *geometric delay*($\tau​$). Since, we know the velocity at which, the plane waves are traveling  i.e speed of light($c​$) , In order to calculate the geometric delay, we need to calculate the extra distance the wave had to travel in order to reach the second antenna. The extra distance would be

​							        	$B.\vec{s_1}$

![](https://casper.berkeley.edu/astrobaki/images/thumb/0/0a/Interferometry_src.jpg/250px-Interferometry_src.jpg)

 

​						So, Geometric delay, ${\tau_1}$ = $\frac{B.\vec{s_1}}{c}$ 

Now, we know the extra time it took this wave to reach the second antenna. Now, we suppose there is a second source in the sky, lets call it $$source_2$$  in the direction of unit vector,  $\vec{s_2}$ . So, for $$source_2$$ we have,

​								${\tau_2}$ = $\frac{B.\vec{s_2}}{c}$ 

So, Antenna$$_i$$ will receive signals from both sources at time $$t$$ and $$antenna_j$$ will receive both the signals at time  $$t-\tau_1$$ and $$t-\tau_2$$  respectively. The antennas themselves can't distinguish themselves between the signals from each source as if they are detecting a combined voltage from both sources. We can actually define the total voltage per antenna  as 

​							$$f=e_1 (t) +e_2(t)= E_i(t)$$ 

Similarly for $$Antenna_j$$ We can have,

​						$$g=e_1(t-\tau_1) +e_2(t-\tau_2)= E_j(t)$$ 

Where $$e_1$$,$$e_2$$,$$E_i$$, $$E_j$$ are the voltage received from source$$_1$$ ,source$$_2$$ and the total voltage at  $$antenna_i$$ and $$antenna_j$$.

So, if we want to find out information about only one source, we need to corelate the signals from each telescope with each other and we run these signals through a correlator which multiplies and integrates the voltages received by the antennae. So, using the correlation equation,

$$f*g(\tau) = \int{f(t)g(t-\tau)}dt$$ 

$$=\int{[e_1(t)+e_2 (t)][e_1(t-\tau_1-\tau) +e_2(t-\tau_2-\tau)]}dt$$ 

​							$$ = \int{e_1(t)e_1(t-\tau_1-\tau)+e_2 (t)e_1(t-\tau_1-\tau) +e_1(t)e_2(t-\tau_2-\tau)+e_2 (t)e_2(t-\tau_2-\tau)}dt$$

Because $$e_1$$ and $$e_2$$ are signals from two different sources are different and independent from each other, they integrate away by averaging to zero as random noise. So the term, 

$$e_2 (t)e_1(t-\tau_1-\tau)$$ and $$e_1(t)e_2(t-\tau_2-\tau)$$ integrates into 0 and we now have,

$$f*g(\tau)= \int{e_1(t)e_1(t-\tau_1-\tau)+e_2 (t)e_2(t-\tau_2-\tau)}dt$$

Now, In order to these term to provide meaningful signal information, they must not be average to zero. This is possible when $$\tau$$ is equal to either negative $$\tau_1$$ or $$\tau_2$$.  $$i.e$$ $$\tau=-\tau_1$$ or $$\tau=-\tau_2$$.

Let's first take for  $$\tau=-\tau_1$$ ,

$$f*g(\tau)= \int{(e_1(t)e_1(t-\tau_1+\tau_1)+0)} dt$$

​		$$= <e_1^2(t)>dt$$

Here the $$e_2$$ term cancels out to be zero as $$\tau_2-(-\tau_1)$$ don't cancel out.

The end result is the average power received by the antennae for either source$$_1$$ or source$$_2$$ depending on the geometric delay.

So, We just showed in a very basic way, how the interferometer works, the telescopes collects the astronomical signals and the correlator matches the signal functions from each antenna with each other so,that they are maximized to give us a power value.

So, this correlation gives us an one dimension image of a sky in a direction parallel to the baseline of the telescope.

Footnotes:

1. http://www.astron.nl/p/WSRT2.htm
2. http://www.cv.nrao.edu/course/astr534/Interferometers1.html
3. https://casper.berkeley.edu/astrobaki/index.php/Basic_Interferometry





