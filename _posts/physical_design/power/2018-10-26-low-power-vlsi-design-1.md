---
layout: post
category: hardware
class: PDN Concepts
title: Low Power VLSI Design Basics (Part 1)
description: Understand power dissipation, types of power dissipation, IR drop, reasons for IR drop and some strategies to minimize IR drop from a VLSI physical design perspective.
author: Gogul Ilango
permalink: /hardware/low-power-vlsi-design-basics-1
image: https://drive.google.com/uc?id=1xyGDoXG5-zywLrc3yOrrnCI02FFD7DxW
cardimage: https://drive.google.com/uc?id=1pNudcK0doHXtomzrx-lhmgK0JBqlbxwD
---

<div class="sidebar_tracker" id="sidebar_tracker">
  <button onclick="closeSidebar('sidebar_tracker_content')">X</button>
  <p onclick="showSidebar('sidebar_tracker_content')">Contents</p>
  <ul id="sidebar_tracker_content">
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_1" href="#power-dissipation">Power Dissipation</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_2" href="#types-of-power-dissipation">Types of Power Dissipation</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_3" href="#dynamic-power">Dynamic Power</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_4" href="#switching-power">Switching Power</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_5" href="#short-circuit-power">Short-circuit Power</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_6" href="#static-power">Static Power</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_7" href="#what-is-ir-drop">What is IR drop?</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_8" href="#types-of-ir-drop-analysis">Types of IR drop analysis</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_9" href="#reasons-for-high-ir-drop">Reasons for high IR drop</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_10" href="#tools-for-ir-drop-analysis">Tools for IR drop analysis</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_11" href="#references">References</a></li>
  </ul>
</div>

Power & Battery life have become very important factors be to considered during chip design as technology node shrinks. For a VLSI Design Engineer, knowledge on power consumption in a CMOS design is crucial as it has become a very big challenge in latest technology nodes.

Almost any electronic device that you hold in your hand (smartphone, tablet, notebook, laptop etc.,) consume power from a limited power supply (battery). Thus, making the chip consume less power is a mandatory problem to be solved.

<h3 class="code-head">Objectives</h3>

```
After reading this tutorial, we will understand
* Why power is important in VLSI design?
* What are the different types of power dissipation?
* What are switching power, short-circuit power and leakage power?
* What is IR drop & different types of IR drop?
* What are the reasons for high IR drop?
* What are the tools available to analyse IR drop?
* What are some strategies to reduce power dissipation?
```

<h3 id="power-dissipation">Power Dissipation</h3>

The process in which a chip produces heat (waste energy) as an unwanted byproduct of its primary action is termed as Power Dissipation. If the chip dissipates power than its maximum limit, it could lead to functionality failure or even burn out. Hence, reducing power dissipation is a necessity in modern semiconductor design due to lower technology nodes, higher frequencies, complex functionalities and portability. 

<h3 id="types-of-power-dissipation">Types of Power Dissipation</h3>

In a low-power CMOS VLSI design, there are two types of power dissipation.

1. Static power
2. Dynamic power

The sources of these power dissipations as well as the techniques to solve them are different. These two types of power dissipation are further classified as shown in Figure 1.

<figure>
  <img src="https://drive.google.com/uc?id=1M1KzqrKbb5k1x_RGBY1-f0QwNbbxd0E3" class="typical-image" />
  <figcaption>Figure 1. Types of Power Dissipation in CMOS</figcaption>
</figure>

<h3 id="dynamic-power">Dynamic Power</h3>

As the name suggests, dynamic power dissipation occurs when the transistors are *switching* from one logic state to another. There are two types of dynamic power dissipation in CMOS circuits namely
1. Switching Power
2. Short-circuit Power

<figure>
  <img src="https://drive.google.com/uc?id=1ogQcgiT94JbFpybC1qmKT2n_7Lf7IH2_" class="typical-image" />
  <figcaption>Figure 2. Types of Dynamic Power</figcaption>
</figure>

<h4 id="switching-power">Switching Power</h4>

When a transistor switch from one logic state to another, the load capacitance at the output pin needs to be *charged* or *discharged* which is referred as the switching power as shown in Figure 2. 
* When the output rises, the load capacitance must go from \\( V_{SS} \\) to \\( V_{DD} \\). 
* When the output falls, the load capacitance must go from \\( V_{DD} \\) to \\( V_{SS} \\).

Recall that in basic electronic theory, there is a *switching current* associated on charging or discharging the capacitor which is given as \\( i = C \frac{dV_{DD}}{dt}\\), which further gets multiplied by \\( V_{DD} \\) to produce power.

Similarly in CMOS, the average dynamic power (\\(P_{dynamic}\\)) is given by 

<div class="math-cover">
$$
\begin{align}
P_{dynamic} & = \frac{1}{T} \int_0^T i_{DD}(t) V_{DD} dt \\
 & = \frac{V_{DD}}{T} \int_0^T i_{DD}(t) dt \\
 & = \frac{V_{DD}}{T} [T f_{sw} C V_{DD}] \\
 & = C V_{DD}^2 f_{sw}
\end{align}
$$
</div>

where 
* \\( f_{sw} \\) - frequency of output switching
* \\( C \\) - load capacitance
* \\( V_{DD} \\) - power supply voltage

#### Switching factor (\\( \alpha \\))

To measure how frequently the output pin of a transistor circuit switches, we define a parameter called switching factor or toggle factor (\\( \alpha \\)). 

If the frequency of output switching is \\(f_{sw}\\), then the charging and discharging cycle will repeat \\(T * f_{sw}\\) times over a time interval \\( T \\).

If \\( f \\) is the clock frequency at which the chip operates, then \\( f_{sw} = \alpha * f \\).

* \\( \alpha = 1 \\) - if the output pin of a transistor switches with the clock frequency.
* \\( \alpha = \frac{1}{2} \\) - if the output pin of a transistor switches once per cycle of the clock frequency.

If we include this switching factor \\( \alpha \\) for dynamic power calculation, we get 

<div class="math-cover">
$$
\begin{align}
P_{dynamic} & = \alpha C V_{DD}^2 f
\end{align}
$$
</div>

Thus, we can reduce dynamic power by 

* Reducing the switching factor \\( \alpha \\) of the transistor.
* Reducing the load capacitance \\( C \\) of the transistor.
* Reducing the supply voltage \\( V_{DD} \\) of the transistor.
* Reducing the clock frequency \\( f \\) of the transistor. 

From an implementation perspective, 

* \\( C \\) comes from <span class="coding">.spef</span> file of the design.
* \\( V_{DD} \\) comes from the chosen <span class="coding">corner</span> of the design.
* \\( \alpha \\) comes from either <span class="coding">.fsdb</span> file or <span class="coding">.gsc</span> file of the design.
* \\( f \\) comes from timing session of the design.

<h4 id="short-circuit-power">Short-circuit Power</h4>

When a transistor switch from one logic state to another, during the signal transition, there exist a *direct path* from \\( V_{DD} \\) to \\( V_{SS} \\) which produces short-circuit current \\( I_{SC} \\) and short-circuit power dissipation. If clock frequency of the design increases, frequency of transition will increase which further increases short circuit power.

Mathematically, short circuit \\( P_{short-circuit} \\) power can be written as 

<div class="math-cover">
$$
\begin{align}
P_{short-circuit} & = I_{SC} * V_{DD} * f_{sw}
\end{align}
$$
</div>

where 
* \\( I_{SC} \\) - short circuit current during signal transition
* \\( V_{DD} \\) - power supply voltage
* \\( f_{sw} \\) - switching frequency

---

<h3 id="static-power">Static Power</h3>

As the name suggests, even when the chip is off or quiescent (static), there exists some amount of power dissipation due to transistor's leakage characteristics giving rise to leakage power. This is due to the characteristic of CMOS transistors itself, which is a function of power supply voltage \\( V_{DD} \\), threshold voltage \\( V_{th} \\) and transistor's dimension (width \\(W \\) and length \\( L \\)). 

<figure>
  <img src="https://drive.google.com/uc?id=1eb4MteRTpf_Me3isJDysUSy5CAo5ofjy" class="typical-image" />
  <figcaption>Figure 3. Static or Leakage Power Dissipation</figcaption>
</figure>

As we scale down the technology node, *leakage power* is becoming a significant contributor in IR drop analysis. Leakage power can further be classified into three types.

1. Diode leakage
2. Sub-threshold leakage
3. Gate-oxide leakage

<div class="math-cover">
$$
\begin{align}
P_{leakage}(V_{DD}, V_{th}, W, L)
\end{align}
$$
</div>

From an implementation perspective, <span class="coding">.lib</span> files of a standard cell contains leakage power related information which is further given to power analysis tools such as Apache RedHawk for power verification.

You can see more information on leakage power [here](https://www.youtube.com/watch?v=d0OxV2rA398){:target="_blank"}.

---

<h3 id="what-is-ir-drop">What is IR drop?</h3>

In a typical chip, power to different blocks, standard cells and macros are provided by the power grid which consists of stack of metal layers (conductors) that run horizontally and vertically in a grid-like fashion over the floorplan. These stacked metal layers have power stripes such as \\( V_{DD} \\) and \\( V_{SS} \\) at regular intervals (pitch) with defined width and thickness, and are connected through vias from one layer to another as shown in Figure 4. This power distribution grid comprises of power rings, power stripes and power rails that are resistive by nature which creates the IR drop. 

<figure>
  <img src="https://drive.google.com/uc?id=1IHjxB0TYTvLJk_eE7qppfdZEvg5nOzve" class="typical-image" />
  <figcaption>Figure 4. Metal layer stack (2D & 3D view)</figcaption>
</figure>

Currently, there are two approaches followed to redistribute power from package to a chip namely [Wire Bonding](https://en.wikipedia.org/wiki/Wire_bonding){:target="_blank"} and [Flip-Chip](https://en.wikipedia.org/wiki/Flip_chip){:target="_blank"} as shown in Figure 5. 

<figure>
  <img src="https://drive.google.com/uc?id=1pNudcK0doHXtomzrx-lhmgK0JBqlbxwD" class="typical-image" />
  <figcaption>Figure 5. Wire-bonding and Flip-chip techniques</figcaption>
</figure>

In flip-chip designs, as power supply voltage gets redistributed from the IO pads to bump pads (containing C4 bump arrays) via top-layer (or [Redistribution Layer](https://en.wikipedia.org/wiki/Redistribution_layer){:target="_blank"} or AP layer), different blocks, standard cells and macros receive power after crossing different metal layers from top to bottom till it reaches the layer in which power pins of the instances reside. 

When power supply voltage travels from top-layer (RDL layer) to power pins layer of instances (usually lower layer), there exists drop in the voltage levels due to the resistive nature of these metal layers. As there is resistance in these metal wires, when a voltage is applied, current is produced which further decreases the voltage level reaching the instances which is termed as the IR drop or Voltage drop.

In addition to the voltage drop that is present in the metal layers stack (on-die), there is also some voltage drop called \\( \frac{di}{dt} \\) drop (off-die) associated with the package leads which has inductance (and less resistance) associated with it due to the time-varying current.

Furthermore, the presence of decoupling capacitors near the instances that store charges locally (which might assist in decreasing voltage drop), adds up some load capacitance. This addition of decaps increases leakage power consumption as well as area which further gets added to the equation.

Thus, we can summarize that the voltage level seen at an instance in the design as

<div class="math-cover">
$$
\begin{align}
V_{instance} = V_{power-supply} - (drop_{metal-stack} + drop_{package-leads} + drop_{decaps})
\end{align}
$$
</div>

From an implementation perspective, if 

* \\( V_{power-supply} = 2V \\) 
* \\( drop_{metal-stack} = 0.2V\\)
* \\( drop_{package-leads} = 0.1V \\)
* \\( drop_{decaps} = 0.1V \\)

then, \\( V_{instance} = 1.6V \\). 

Any instance in the design will have a maximum voltage drop limit above which it may fail in functionality or timing. So, it's the job of the engineer to reduce IR drop in the design before tapeout.

<h3 id="types-of-ir-drop-analysis">Types of IR drop analysis</h3>

There are two standard types of IR drop analysis for a circuit design namely 
1. **Static IR drop** - Vectorless IR drop analysis with average current cycles. Typically used for Electro-Migration (EM) analysis where current limit is checked for wires. 
2. **Dynamic IR drop** - Vectorless or VCD based IR drop analysis with worst-case switching currents. Typically used to check voltage drop limit for switching instances.

| Static IR Drop                                                                                  | Dynamic IR Drop                                                                                                                                                       |
|-------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| All cell instances will draw average current (DC).                                              | All switching instances will draw transient current (AC). All non-switching instances will draw only leakage current.                                                 |
| Total Average demand will be much lesser than real peak demand current for the design.          | Real peak demand current is measured and analyzed in dynamic IR.                                                                                                      |
| Total demand current is supplied from the power source (battery).                               | Total demand current is supplied from the power source (battery) and some portion of the demand current is supplied by decoupling capacitors near the cell instances. |
| All cell instances will draw current all the time. Hence, switching effects are not considered. | Switching effects are always considered. All instances draw transient current only during switching. Simultaneous switching causes huge peak demand current.          |
| If package is considered, there is no IR drop due to Ldi/dt effects as current is constant.     | If package is considered, Ldi/dt effects are considered.                                                                                                              |

<h3 id="reasons-for-high-ir-drop">Reasons for high IR drop</h3>

Some of the standard reasons for high IR drop in a design are 

* High power grid resistance.
* High current flowing through the power grid.
* Simultaneous switching of instances at same time.
* Less amount of decoupling capacitors near the instances.
* High parasitics in package leads.
* Lesser length or width of power stripes in RDL layer.
* Lesser power sources such as power bumps (in flip-chip).
* Incorrect input files such as <span class="coding">.lef</span>, <span class="coding">.def</span>, <span class="coding">.lib</span>, <span class="coding">.spef</span>, <span class="coding">.sta</span>, <span class="coding">.ploc</span> or <span class="coding">APL</span> files.

<h3 id="tools-for-ir-drop-analysis">Tools for IR drop analysis</h3>

There are different tools available to perform IR drop analysis for a design from physical design perspective. Some of the industry standard tools are [Apache RedHawk](https://www.ansys.com/products/semiconductors/ansys-redhawk){:target="_blank"} and [Cadence VoltageStorm](https://www.slideshare.net/AlanTran3/voltagestorm){:target="_blank"}. 

In Apache RedHawk, we can do static as well as dynamic IR drop analysis. Also, we can analyze the power grid of the design and find out weaknesses such as shorts, opens, missing vias etc., before performing actual IR drop analysis.

After completing IR drop analysis for a design in RedHawk, we can review and analyze different types of maps such as Average IR drop map, Frequency map, Load capacitance map etc., and reports dumped by RedHawk to check for potential issues in the design. 

<h3 id="conclusion">Conclusion</h3>

In this tutorial, we looked at saving power from a physical design perspective. We have understood the different types of power dissipation in a CMOS based circuit design, understood what is IR drop at physical level, why IR drop occur at physical level, what are some techniques to reduce IR drop at physical level and tools available to analyze IR drop.

<h3 id="references">References</h3>

* [Low Power VLSI Design](https://www.youtube.com/watch?v=TFOO1JAll2Y){:target="_blank"}
* [Power Consumption](https://semiengineering.com/knowledge_centers/low-power/low-power-design/power-consumption/){:target="_blank"}
* [IR Drop Analysis using RedHawk](http://www.vlsi-basics.com/2013/10/ir-drop-analysis-using-redhawk-overview.html){:target="_blank"}
* [An efficient RDL routing for flip-chip designs](https://www.edn.com/design/systems-design/4419930/An-efficient-RDL-routing-for-flip-chip-designs){:target="_blank"}
* [Novel and efficient power grid design for lesser metal layer process SOC's](https://www.design-reuse.com/articles/31011/power-grid-design.html){:target="_blank"}
* [IR Drop Analysis Interview Questions](http://www.vlsi-basics.com/2013/12/ir-drop-analysis-interview-questions.html){:target="_blank"}
* [Minimizing Leakage Power - I](https://www.youtube.com/watch?v=SvZOq2B3-pg){:target="_blank"}
* [Minimizing Leakage Power - II](https://www.youtube.com/watch?v=lnDjc_4UB6M){:target="_blank"}
* [Leakage Power Trends](http://asic-soc.blogspot.com/2008/03/leakage-power-trends.html){:target="_blank"}