---
layout: post
title: "Quantum Interference in Transport through Single Molecules"
date: 2015-03-10 12:00
comments: true
categories: [Science, Chemistry, Quantum Transport, Interference, Molecular Electronics]
---

In this post I will give a pedagogical explanation of how quantum mechanics influences the electronic conductance of a single molecule.

The setup -- which have been realized in many labs around the world -- involves a nano-meter-sized gold bridge, which is very carefully broken in order to create a nano-meter-sized gap. Pour molecules onto this golden gap and pray that one of them will be caught in the gap, forming a very delicate molecular bridge. The transport properties of the molecule is then characterized by applying a voltage drop across this molecular junction and measuring the current response.

While electrons are normally thought of as particles, they will -- due to quantum mechanics -- also behave as waves. And what we seek to explain in this post, is how the wave nature of the electrons affects the transport properties of the molecular junction.

### The two slit experiment

The most well-known wave property is **interference**, and our aim is to understand how interference can affect the electronic properties of molecular bridges. The main example of interference is the popularized two-slit-experiment:

{% img center /files/interference_in_transport_through_single_molecules/01-doubleslit.png 'The Double slit experiment' 'Double slit experiment' %}

In the double slit experiment a wave originating on the left, passes through two slits and the wave intensity at some point in space is then detected by a detector. Here we will investigate what happens as we simultaneously change the position of the detector and the wave source on the vertical axis. 

1. In the middle between the two slits, the two paths are of equal length. The wave passing along those two paths share the same phase meaning that the waves *add*, and this phenomena is known as **constructive interference**. 

2. If we move both the source and the detector we encounter a different scenario. When the difference in path lengths exactly matches half a wavelength, the wave passing along the two paths is out of phase, and the waves *substract* -- an effect known as **destructive interference**. 

{% img center /files/interference_in_transport_through_single_molecules/02-constructivedestructive.png 'Constructive and destructive interference' %}

In fact, the wave intensity measured by the detector can be plotted as a function of the vertical displacement, *y*. The resulting *transmission* shows a characteristic interference pattern with valleys and hills corresponding to destructive and constructive interference effects. You may also note that when the source and the detector aligns with one of the slits, we may have perfect direct transmission:

{% img center /files/interference_in_transport_through_single_molecules/03-dsintensity.png 'Constructive and destructive interference and direct transmission' %}

### Molecules

We are interested in transport through molecules. As we shall see, the molecular bridge can be thought of more or less like the two-slit-experiment that we just discussed. However, in molecular electronics we cannot control the actual vertical displacement of the electronic wave passing through the molecular bridge. Instead we have -- through the bias voltage and perhaps a small electro-static gate -- another very precise handle which we can control: **The energy**. In the following we will only look at situations where the energy of each electron passing through the molecule is conserved. That means that we cannot gain or loose energy by interacting with the electrodes, the molecule, the substrate or anything else in the setup. 

Now, an electron enter the molecule enter with a certain energy, and it leaves with the exact same energy. This makes the energy equivalent to the vertical displacement, we discussed in the double slit experiment. This also means that it does not help us very much to look at only the molecular structure in real-space. In fact it is highly non-trivial to understand the wave-coherent transport through a molecule by just looking at the physical positions of the atoms in the molecule. 

For simplicity we will constrict ourselves to a certain class of molecules: [conjugated organic molecules](https://en.wikipedia.org/wiki/Conjugated_system). Conjugated organic molecules have a backbone of carbon atoms, which are strongly bound together by sigma bonds. In conjugated molecules those sigma-bonds all lie in the plane, and perpendicular to this plane a single $p_z$ orbital sticks out from each carbon atomic site. 

This $p_z$ orbital carries a single electron. The $p_z$ electrons are allowed to hop and *delocalize* over the entire system of $p_z$ orbitals. We call this system of orbitals and electrons for the **pi-system**. It is those pi-systems that we will consider in the following.

We may diagonalize the Hamiltonian governing the electronic pi-system, and find the eigenenergies and the eigenstates. The eigenstates can for simplicity be thought of as molecular orbitals, where each orbital can accommodate up to two electrons (depending on their spin). 

Let us make these concepts more tangible by considering the pi-system of 1,3-butadiene. In the following figure we show how this molecule is put together, we show the schematic and the molecular orbitals as a function of energy. Note that the molecular orbitals have different colors, which actually correspond the sign of the wavefunction - actually the *phase*.

{% img center /files/interference_in_transport_through_single_molecules/08-butadiene.png '1,3-butadiene and its molecular orbitals' %}

You may also note that we have filled up the molecular orbitals with the four available electrons (here drawn as up and down arrows). This fact will become important as we enter the next section.

### Transport through molecules

We are now able to to look at our molecule in energy space, and we are now ready to perform a simple transport experiment. Am electron source sends in electrons with a certain energy. The electrons are then then transmitted through the molecule and obtain a phase given by the molecular orbital, which it passes through. Like in the double slit experiment, the electrons are allowed to pass through slits which does not match the energy, as long as they end up with the same energy after the process.

Lets splash some electron-waves on 1,3-butadiene and see what we get:

{% img center /files/interference_in_transport_through_single_molecules/04-molintf1.png 'Transport through 1,3-butadiene' %}

As you can see, the electronic wave-packets have been colored according to the phase they have at each stage of the transport process. This is obviously true for the transport processes which happen through the unoccupied orbitals (with positive energy). Here the electron is added to the molecule, propagates, and is finally removed.

However, the electrons cannot move through the orbitals already occupied by electrons (negative energy). Instead one must take out an electron, allow the *hole* to propagate and then add the incoming electron. Because electrons are fermions this reversal of the process gives an additional sign relative to transport through unoccupied orbitals.

Looking at the phases, we expect to find constructive interference at zero energy. Here comes the transmission as a function of energy:

{% img center /files/interference_in_transport_through_single_molecules/05-molintf1intensity.png 'Transport through 1,3-butadiene as a function of energy' %}

Not many surprises there. This would be almost indistinguishable to the case where we interpreted the electrons as being classical particles. The hallmark of wave interference is really the presence of destructive interference. So let us look at a slightly different molecular junction.

{% img center /files/interference_in_transport_through_single_molecules/06-molintf2.png 'Transport through cross-conjugated system' %}

Again the colors correspond to the wave-function phase, and the hole transport processes have gotten an extra sign because of fermionic exchange. In this case we see that the contributions are out of phase, and so we expect the transmission to vanish at zero energy. Lo and behold&hellip;

{% img center /files/interference_in_transport_through_single_molecules/07-molintf2intensity.png 'Transport through cross-conjugated system as a function of energy' %}

Now, *fermionic exchange* refers to how the exchange of two fermions (electrons are fermions) produces an additional sign. In this scattering setup two different processes take place. If the electronic wave moves through the unoccupied (unfilled) orbitals, the electron first enters the molecular orbital on the left and then leaves it on the right. For the filled orbitals the 

 involving the un-filled orbitals we first add and then remove an electron on the other side. For the filled orbitals we must switch the process around and remove an electron before we can add one from the electron source.

### One question and one answer

So, we have shown how quantum interference happens in molecular systems by creating a clear analogy with the well-known double slit experiment. You may wish to try your understanding a bit, so let me ask some questions to help you along:

- The direct transmission peaks are aligned with the molecular eigenenergies. So beyond those peaks you begin to probe the phase between different molecular orbitals. Try as you may, to explain the absence of destructive interference features between the two nearest molecular orbitals. It may not be obvious at first.

You may also wonder how this picture changes when you add Coulomb repulsion between the electrons. The funny thing is that not much changes, because in this case one can paraphrase the explanation in terms of the Feynman-Dyson many-body orbitals. You can read more about those generalized molecular orbitals in [this publication](http://arxiv.org/abs/1403.4056) of mine.





