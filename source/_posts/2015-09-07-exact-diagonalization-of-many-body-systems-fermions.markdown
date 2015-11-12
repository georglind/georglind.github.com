---
layout: post
title: "Exact diagonalization of Many-body systems: Fermions"
date: 2015-09-07 13:29
published: false
comments: false
categories: [Physics, Programming, Numerics, Quantum mechanics]
---

In the following two post, I'm going to to my best at explaining exact diagonalization of some lattice systems. In this first 

So why would one like to do exact diagonalization. Well, one probably has something like a Hubbard model described by the Hamiltonian,...

We are going to use an example to work our way through exact diagonalization. In our case we are going to look at electrons on a lattice. The electrons come in two flavors: spin up and spin down. Electrons are fermions and so they obey the Pauli principle, which basically means that no two fermions can reside in the same single particle state. 

Our system is described by a Hamiltonian in two parts, 

$$
	H = \sum_{\langle i, j \rangle} \sum_{\sigma \in \{\uparrow, \downarrow\}} \left( t_{ij} \, \hat{c}^\dagger_{\sigma i} \hat{c}^{\phantom{\dagger}}_{\sigma j} + \text{h.c.}\right) + U \sum_{i} \hat{n}_{\uparrow i} \hat{n}_{\downarrow i}.
$$

The first part described how the electrons are free to hop between different sites in the lattice. Here we are not going to distinguish how spin-up electrons and spin-down electrons hop. 

The second term describes how electrons residing on the same site experience a repulsion due to the Coulomb interaction between the two negative charges. Notice that this interaction happens between a spin-up and a spin-down electron. This is because the Pauli principle prohibits two spin-up electrons to inhabit the same lattice site. 

Now, it is this second part which complicates matters. Due to the interaction between electrons we will have to consider the full many-body wavefunction. With the interaction absent the electrons would not be able to "see" each other, and we could then solve the behavior of each electron separately.

Let us label our sites from $i = 1\ldots N$. Then we may write some many-body state like this,

{% img center /files/exact_diagonalization/fermi_hubbard/fermihubbard-01.png 'The fermionic many-body state: [u0, 00, ud, u0, 00, 0d, ..., ud, 0d] with "u" referencing up and "d" down.' %}

The problem is to represent such state numerically. We are going to use a very efficient method originally due to ?? Lin and simply called Lin tables. The idea is quite simple, If you have a many-body system which naturally separates into two distinct systems,


We have implemented this solution in a small library that we simply call fermihubbard.py. It is hosted on github.com. Please take a look.


