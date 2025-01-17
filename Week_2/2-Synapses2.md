(synapses-2)=
# Synapses 2

[Download the slides here](slides/W2-V1-synapses-2.pptx)

:::{iframe} https://www.youtube.com/embed/SI3FalfSZVI
:width: 100%
:::
---

## Introduction

In the [last section](#synapses1-page), we covered [synapses](#chemical-synapses), [neurotransmitters](#neurotransmitters-paragraph), and [receptors](#receptors). 

:::{attention} Note!
In this section, we're going to cover how synapses can adjust their strength and weight.
:::

(hebbian)=
## Hebbian Learning

In general, we train artificial neural networks by adjusting their connection weights according to a learning rule, but what is the equivalent in biology?

Well as early as 1949 [Donald Hebb](https://en.wikipedia.org/wiki/Donald_O._Hebb) proposed a relevantly simple learning rule: 

_"When an axon of cell A is near enough to excite a cell B and repeatedly or persistently takes part in firing it, some growth process or metabolic change takes place in one or both cells such that A’s efficiency, as one of the cells firing B, is increased."_

At the time this was just a theory, but experimental evidence confirmed it around 20 years later.
This is often summarised as _'Cells that fire together wire together, and conversely Cells that fire out of sync lose their link'._
Though this misses the fact that cell A must spike first to contribute to B's firing, therefore the relative timing matters. 

## Spike-timing-dependent Plasticity

Let's consider a pair of neurons. In the [figure below](#Synapses2Picture1), panel A illustrates that if the pre-synaptic neuron's spike occurs before or after the post-synaptic neuron, their relationship is causal or acausal. Panel B shows how this synapse's strength (on the y-axis) will be adjusted depending on the difference in spike timing between the two neurons. If the relationship is casual, so 'pre' precedes 'post' the strength will be increased or potentiated (shown in green). While if it is acausal, so 'pre' tends to follow 'post', then the strength will be decreased (shown in red).

```{figure} figures/Synapses2Picture1.jpg
:label: Synapses2Picture1
:width: 330px
:align: center

Spiking-timing-dependent plasticity (See [paper](https://doi.org/10.3389/fnsyn.2011.00004))
```

This is known as spike-timing-dependent plasticity, and it tends to induce long-term changes in synaptic strength via processes known as **long-term potentiation** (LTP) and **long term depression** (LTD).

:::{hint} Linker
So, what changes at the synapse to cause this change in weight?
:::

## Altering Synapses

If we think about the structure of the synapse, then we can see that there are many possibilities for changing the connection strength such as:

* Increasing the number of synaptic vesicles or density of neurotransmitters
* Increasing the number of post-synaptic receptors
* Increasing the surface or even adding an additional synapse between the two neurons.

But these are long-term changes, and synaptic weights can also change on much quicker timescales, on the order of hundreds to thousands of milliseconds. This is known as short-term plasticity.

```{figure} figures/Picture3.png
:label: synapse
:width: 500px
:align: center

Synapse
```

## Short-term Plasticity

Short-term plasticity describes how synaptic strength dynamically changes with the level of presynaptic activity. Broadly, short-term facilitation is caused by the higher levels of calcium at the axon terminal after spiking, which increase the probability of neurotransmitter release. 

Short-term depression is caused by the lower levels of neurotransmitters available at the synapse, and in an extreme case, it's possible that the synapse will fail to send a signal at all. 

Hence, short-term plasticity shows how a neuron's recent activity and the state of it's synapses influence it's weight dynamically. The fact that synapses will sometimes fail to send a signal may remind you of drop-out in machine learning, though in this case, individual connections are failing, not the entire unit. Yann Le Cun and colleagues explore this difference in a paper which you can read [here](http://dx.doi.org/10.4249/scholarpedia.3153).

```{figure} figures/Synapses2Picture2.png
:label: depressionsynapse
:width: 500px
:align: center

Synapse short-term depression
```

## DropConnect

Just to be explicit:

* Dropout - randomly silence **units** during training, which reduces over-fitting.
* DropConnect - randomly silence **weights**

Just to give you a quick comparison between the two, the [graph below](#Synapses2Picture3) shows the text error on [MNIST](https://en.wikipedia.org/wiki/MNIST_database) as a function of the network size, with the following plots:

* No-Drop in black - the error increases with size as the network increasingly overfit
* Dropout in red - the error decreases with size
* DropConnect in blue - the error is lower and more stable.

```{figure} figures/Synapses2Picture3.png
:label: Synapses2Picture3
:width: 500px
:align: center
```
:::{seealso} For more!
:class: dropdown 
{cite:t}`Wan2013` provides more empirical and theoretical results which suggest that DropConnect may be advantageous.
:::

:::{seealso} That's it!
In the next section we will go through how neurons connect together to form networks and circuits.
:::