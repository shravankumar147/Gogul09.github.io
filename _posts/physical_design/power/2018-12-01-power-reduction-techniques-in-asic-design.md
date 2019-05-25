---
layout: post
category: hardware
class: PDN Concepts
title: Power Reduction Techniques in ASIC Design
description: Understand what are power domains, power management cells, power management IC, advanced low power techniques and much more related to power distribution in a VLSI design.
author: Gogul Ilango
permalink: /hardware/power-reduction-techniques-in-asic-design
image: https://drive.google.com/uc?id=1TsYhJZdSqldmF8aEiM4pMP54EldLgCfb
cardimage: https://drive.google.com/uc?id=1xj9hjf0jS1mDQ4v6_iUQKDuE8hRcakvD
---

<div class="sidebar_tracker" id="sidebar_tracker">
  <button onclick="closeSidebar('sidebar_tracker_content')">X</button>
  <p onclick="showSidebar('sidebar_tracker_content')">Contents</p>
  <ul id="sidebar_tracker_content">
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_1" href="#power-domains">Power Domains</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_2" href="#voltage-islands">Voltage Islands</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_3" href="#power-management-cells">Power Management Cells</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_4" href="#power-management-unit">Power Management Unit</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_5" href="#advanced-low-power-techniques">Advanced Low Power Techniques</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_6" href="#esd-cells">ESD Cells</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_7" href="#references">References</a></li>
  </ul>
</div>

When it comes to reducing power dissipation in a chip, there are different techniques followed in industry at different levels of abstraction (circuit-level, logic-level, physical-level etc.,). In this blog post, we will focus on physical-level power management techniques and industry jargons related to power management in chip design.

Before proceeding with this tutorial, kindly read [Power Distribution Network in ASIC Physical Design](https://gogul09.github.io/hardware/power-distribution-network-in-asic-physical-design){:target="_blank"} so that you get to know some of the basic concepts needed to understand the concepts that we will discuss in this tutorial.

<div class="objectives">
  <h3>Objectives</h3>
  <p>After reading this tutorial, we will understand</p>
  <ul>
    <li>What are power domains?</li>
    <li>What are voltage islands?</li>
    <li>What are power management cells?</li>
    <li>What is a power management unit?</li>
    <li>What are ESD cells?</li>
    <li>What are some of the advanced low power techniques?</li>
  </ul>
</div>

<h3 id="power-domains">Power Domains</h3>
Imagine we have four IPs (blocks or hard-macros) of different functionality in a chip. Let's say <span class="coding">IP1</span> is a CPU, <span class="coding">IP2</span> is a Graphic Processor, <span class="coding">IP3</span> is an Audio Processor and <span class="coding">IP4</span> is a Power Management Unit (mixed signal). Based on its functionality, we can say that
* <span class="coding">IP1</span> is a **timing-critical** block and operates at highest frequency as it's the CPU. Let's say it operates at 1.2V. 
* <span class="coding">IP2</span> and <span class="coding">IP3</span> are **switchable** blocks i.e. we can switch off power to these blocks to save some power. Let's assume these two operates at 1.5V.
* <span class="coding">IP4</span> is an **always ON** block that needs to be ON all the time as it manages the power supply. Let's say it operates at 3.1V.

<figure>
  <img src="https://drive.google.com/uc?id=1xj9hjf0jS1mDQ4v6_iUQKDuE8hRcakvD" class="typical-image" />
  <figcaption>Figure 1. Power Domains (Multi-voltage design)</figcaption>
</figure>

A power domain is a **logical** (virtual) portion of the design in which the logic cells in that power domain share common power supply characteristics. Each hierarchical cell in the design can belong to only one power domain. 

Defining power domains on logical hierarchical boundaries is the ideal and preferred approach instead of defining power domains for logical hierarchies that are different.

In our case, <span class="coding">IP1</span> belongs to <span class="coding">PD1</span> (or Power Domain 1), <span class="coding">IP2</span> belongs to <span class="coding">PD2</span>, <span class="coding">IP3</span> belongs to <span class="coding">PD3</span> and <span class="coding">IP4</span> belongs to <span class="coding">PD4</span> (each power domain shown in different colors in Figure 1).

Also note that, a power domain is purely logical and not physical. To realize power domains physically, we define **voltage islands** or **voltage areas** in the physical layout.

<h3 id="voltage-islands">Voltage Islands</h3>
Voltage island is a physical realization of a power domain in a design. In our case, all the different IPs will have their dedicated rectilinear coordinates that defines the island boundaries, power mesh structure and switching characteristics of each power domain, respectively (as shown in Figure 1). Power mesh and switching characteristics for <span class="coding">IP1</span> can be different than other IPs and vice-versa.

Logic cells that talk within their own power domain has no power constraint. But cells that have signals that communicate from one power domain to another, say <span class="coding">IP1</span> to <span class="coding">IP3</span> requires special power management cells such as isolation cells and level shifters.

<h3 id="power-management-cells">Power Management Cells</h3>

To reduce power consumption and to protect interfaces between power domains, there are special types of standard cells defined in library such as isolation cells, level shifters, retention registers, power switch and always ON buffers as shown in Figure 2.

<figure>
  <img src="https://drive.google.com/uc?id=1aqYbDcGJGHs9LqLWRfyH3sxc1O6CWSi0" class="typical-image" />
  <figcaption>Figure 2. Power management cells to reduce power consumption</figcaption>
</figure>

#### Level Shifters

If a signal from <span class="coding">IP1</span> talks to <span class="coding">IP3</span>, we need a level shifter which shifts this signal's voltage level from **2V** to **1.5V**. Level shifters are special power management cells that has two power supply nets.

1. Input supply net - connected to the voltage supply of driver's power domain.
2. Output supply net - connected to the voltage supply of receiver's power domain.

There are two types of level shifters namely buffer-type level shifters and enable level shifters. Level shifters must be checked for proper drive strength and accurate timing as signals are transitioned from one voltage level to another voltage level.

#### Isolation Cells

If a signal from switchable <span class="coding">IP2</span> block talks to always ON <span class="coding">IP4</span> block, then if <span class="coding">IP2</span> is powered off, all the outputs of <span class="coding">IP2</span> power domain will be in an unknown state **X**. Thus, we need to properly **isolate** these unknown output **X** values to protect always ON power domain <span class="coding">IP4</span>. Connecting a shut-down logic and active logic can also cause design issues such as spurious signal propagation and crow-bar current.

Thus, isolation cells are added to the switchable power domain <span class="coding">IP2</span>. These isolation cells are AND/OR gates where one input is the output of a cell in switchable domain (which might cause **X** propagation) and other input is a controlling value (from always ON domain) to prevent unknown state propagation to always ON domain. 

#### Power Switches

As shrinking technology node increases leakage power, we need power switches to turn off power to CMOS transistors when they aren't switching. When the logic in a power domain is inactive, we can turn off the power to this power domain using a power switch to save leakage power.

Power switches are added between the main supply and the virtual supply to be shutdown. The virtual supply is the power supply to standard cell supply rails.

#### Retention Registers

There are cases in which you wish to retain the states of sequential cells in a switchable power domain, say <span class="coding">IP2</span>, even when its turned off. To retain the state values of sequential elements, retention registers are used.

These registers hold the state of sequential cells in that power domain even when power is turned off. In layout, it's viewed like randomly glowing bulbs in darkness.

One tradeoff in using retention registers is that it needs extra area as well as extra routing resources (power + signal) in the design.

#### Always ON buffers

When power is turned off for a switchable domain, say <span class="coding">IP3</span>, there might be cases where some logic needs to be active during shutdown. These logic includes control signals to retention registers or power switches as well as enable signals to isolation cells or level shifters. Sometimes it could also be signals in the feedthrough paths that travel from one power domain to another.

In these cases, always ON buffers or inverters are used which remain active during shutdown. There are two types of always ON cells such as 

1. Single rail always ON cells
2. Dual rail always ON cells

<h3 id="power-management-unit">Power Management Unit (PMU)</h3>

Multi-supply voltage techniques (using power domains) as discussed above can reduce power consumption of a chip as not all the blocks in the design needs exact power supply from a battery (most blocks are made switchable). If we have multi-supply voltage values for each power domain in our design, how does the single power supply that comes out from our battery gets transformed into different voltage levels? 

The answer is **Power Management Unit (PMU)** or **Power Management Integrated Circuit (PMIC)** - [\[wikipedia\]](https://en.wikipedia.org/wiki/Power_management_integrated_circuit){:target="_blank"}.

A dedicated power management unit takes in single power supply from our battery and produces the necessary voltage levels needed for the design. This PMU can be a part of a chip (such as <span class="coding">IP4</span>) or outside the chip (a dedicated IC called PMIC) depending on packaging and cost requirements. 

A typical power distribution network for a smartphone or tablet or any other gadget uses a PMU or a PMIC to convert single battery power supply into different block-level power supplies which is controlled by the operating system through I2C or any other protocol as shown in Figure 3.

Two main components in a [PMIC](https://en.wikipedia.org/wiki/Power_management_integrated_circuit){:target="_blank"} are 

1. [DC-DC converter](https://en.wikipedia.org/wiki/DC-to-DC_converter){:target="_blank"}, an electronic circuit that converts a source of Direct Current (DC) from one voltage level to another. 
2. [Low Dropout Regulator](https://en.wikipedia.org/wiki/Low-dropout_regulator){:target="_blank"}, a linear DC electronic circuit that can regulate the output voltage i.e. make the output voltage steady.

Based on the functionality, DC-DC converters are further divided into

1. Buck converters (Step-Down)
2. Boost converters (Step-Up)
3. Buck-Boost converters

<figure>
  <img src="https://drive.google.com/uc?id=1zEiAP5_7NjbVpt01zbE-7Fq3ZRpxbFAl" class="typical-image" />
  <figcaption>Figure 3. Power Distribution Network in a smartphone</figcaption>
</figure>

<h3 id="advanced-low-power-techniques">Advanced Low Power Techniques</h3>

Some of the commonly used advanced low power techniques to reduce power consumption in CMOS are shown in Figure 4. All the below mentioned advanced power optimization techniques require knowledge of something called as [UPF](https://en.wikipedia.org/wiki/Unified_Power_Format){:target="_blank"} or Unified Power Format which is the IEEE standard followed in industries to specify power intent of a design. We will learn about UPF in a separate blog post.

<figure>
  <img src="https://drive.google.com/uc?id=1Sst6kPRCsc3r0_A1ia_VyEeNz386iwxV" class="typical-image" />
  <figcaption>Figure 4. Advanced Low Power Techniques</figcaption>
</figure>

#### 1. Multi-voltage design

This technique assigns different voltages (power domains) for different regions in the design where these different voltages levels are obtained or controlled using a PMIC or PMU. The interfaces between different power domains need to be managed using level shifters and/or isolation cells. This technique reduces dynamic power.

#### 2. Power Gating (Shutdown)

This technique uses a single voltage throughout the design with switchable regions which can be turned off to reduce power. Switching off and switching on power requires power switches which are MTCMOS cells which uses LVT during normal mode (to reduce short circuit power) and uses HVT during off mode (to reduce leakage power).

Again these power switches requires control signals from a PMIC or PMU. This technique greatly reduces leakage power as some blocks are completely switched off when their functionality is not needed.

Due to higher load in multi-million instance based design, large amount of inrush current flows to charge the internal capacitors. To reduce this inrush current, power switches are placed in a daisy chain like arrangement. 

#### 3. Multi-voltage + Power Gating (Shutdown) with State Retention

This technique combines the above two approach with **state retention registers** in the switchable regions of the design. This is the most commonly used approach to reduce power consumption of a chip. This techniques reduces both dynamic and leakage power.

Furthermore, from a physical design perspective, the power grid in top-level needs to be aligned with the power grid in block-level. This needs proper selection of pitch, width and spacing between metals in the power grid. Due to these constraints, there is **IR drop** in each block and so, power analysis (static + dynamic) needs to be clean at these blocks for signoff - [read more](https://www.edn.com/design/integrated-circuit-design/4440822/SoC-PDN-challenges-and-solutions){:target="_blank"}. 

#### 4. Dynamic Voltage & Frequency Scaling (DVFS)

This technique uses a separate control unit to control power to different regions in a design so that voltage levels are adjusted dynamically or adaptively based on functionality. Again there is a tradeoff in area for the power control circuitry. Apart from adjusting voltage levels, frequency can also be dynamically adjusted where performance is not a priority, thereby saving some power.

<h3 id="esd-cells">ESD Cells</h3>

Due to shrinking feature sizes and increasing metal layer stack, Electro-Static Discharge (ESD) has become another major concern for low-power VLSI designs. Due to static electricity that could be produced in any uncontrollable exposed environment such as Human Body Interaction (HBM), Machine Handling (MH) or from internal build-up of charge leaving through the package (CDM or Charged Device Model), chip shouldn't get exposed and affected due to these factors. 

ESD or Electro-Static Discharge cells are **clamp circuits** that are placed at appropriate locations inside the chip to provide a low impedance discharge path for the ESD current, handle large transient current and clamp the signal voltage at a level that avoids dielectic breakdown. In modern chip design, ESD cells are mandatory to avoid functional failure or burn out of the chip.

[Apache RedHawk](https://www.ansys.com/en-in/products/semiconductors/ansys-redhawk){:target="_blank"} is the industry standard tool to comprehensively analyse, plan and verify ESD at full chip-level that ensures connectivity between any two pins meets design guidelines. [Apache's PathFinder](https://www.apache-da.com/products/redhawk/pathfinder){:target="_blank"} is capable of performing ESD connectivity analysis for HBM, MM and CDM ESD events and predicts the current density in all metal wires and vias - [read more](https://www.semiwiki.com/forum/content/2933-full-chip-esd-sign-off-necessary.html){:target="_blank"}.

<h3 id="references">References</h3>

* [Power Intent Formats: Power Domain](https://semiengineering.com/power-intent-formats-power-domain/){:target="_blank"}
* [Power Domain Crossings](http://vlsi-soc.blogspot.com/2017/02/power-domain-crossings.html){:target="_blank"}
* [Voltage Islands](https://semiengineering.com/knowledge_centers/low-power/techniques/voltage-islands/){:target="_blank"}
* [Power management integrated circuit](https://en.wikipedia.org/wiki/Power_management_integrated_circuit){:target="_blank"}
* [Power Management Cells](https://www.youtube.com/watch?v=aOLPIFNESgg){:target="_blank"}
* [Power Domains](https://www.youtube.com/watch?v=4asqcmyavos){:target="_blank"}
* [Power Management Integrated Circuits: Keep the Power in Your Hands - Quentin Schulz, Free Electrons](https://www.youtube.com/watch?v=GsDWgm0YiaU){:target="_blank"}
* [Electro-static Discharge (ESD)](https://www.semiwiki.com/forum/content/546-electro-static-discharge-lesdl.html){:target="_blank"}
* [Advanced Low Power Terminology](https://www.youtube.com/watch?v=mMwwoFtuQKE&list=PL602848A2E518E963&index=8){:target="_blank"}