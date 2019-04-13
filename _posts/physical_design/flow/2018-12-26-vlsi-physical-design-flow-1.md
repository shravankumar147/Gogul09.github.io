---
layout: post
category: hardware
class: PD Concepts
title: VLSI Physical Design Flow
description: Understand the fundamentals in VLSI Physical Design Flow such as Floorplanning, Partitioning, Placement, Clock Tree Synthesis, Routing, Timing Verification, Power Verification, Formal Verification and Physical Verification.
author: Gogul Ilango
permalink: /hardware/physical-design-flow-1
image: https://drive.google.com/uc?id=1amQI_tQSrnTqYAXhraVpNc1NpJVgPNTE
cardimage: https://drive.google.com/uc?id=1FgocjfTQNYG5MJF8g17_WQzb-3ss1aBG
---

<div class="sidebar_tracker" id="sidebar_tracker">
  <button onclick="closeSidebar('sidebar_tracker_content')">X</button>
  <p onclick="showSidebar('sidebar_tracker_content')">Contents</p>
  <ul id="sidebar_tracker_content">
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_1" href="#what-is-vlsi-physical-design">What is VLSI Physical Design?</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_2" href="#why-vlsi-physical-design-flow">Why VLSI Physical Design Flow?</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_3" href="#vlsi-physical-design-flow">VLSI Physical Design Flow</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_4" href="#importing-inputs">Importing Inputs</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_5" href="#floorplanning-and-partitioning">Floorplanning & Partitioning</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_6" href="#power-planning">Power Planning</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_7" href="#placement">Placement</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_8" href="#clock-tree-synthesis">Clock Tree Synthesis</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_9" href="#routing">Routing</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_10" href="#static-timing-analysis">Static Timing Analysis</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_11" href="#power-verification">Power Verification</a></li>
  </ul>
</div>

When I was a kid, I used to spend time with playstation and computers. At that time, I always wondered how those tiny components inside rectangular black boxes entertain me by making me play cool games and watch movies. When I grew up, I realized its the combination of [logic design](https://www.britannica.com/technology/logic-design){:target="_blank"} and [physical design](https://en.wikipedia.org/wiki/Physical_design_(electronics)){:target="_blank"} that makes an Integrated Circuit that is sitting inside the device you currently hold in your hand.

In this blog post, we will learn the basics of VLSI physical design or VLSI backend design that is used to create modern Integrated Circuits (ICs) that power up numerous electronic applications such as desktop, laptop, tablet, smartphone etc.

<h3 id="what-is-vlsi-physical-design">What is VLSI Physical Design?</h3>

The final output of a frontend design or circuit design or logic design is a [netlist](https://en.wikipedia.org/wiki/Netlist){:target="_blank"}. Netlist contains the logical functionality of your chip. This netlist could be viewed as a plethora of instances with interconnections (nets) between them based on the functionality you wish to implement. 

This connectivity information in a netlist is a layer of abstraction of your hardware which must be converted to a physically realizable format (having geometric shapes) that is manufacturable. 

> The process of converting a gate-level netlist (written using a Hardware Description Language) into a physically realizable format (GDSII) which finally becomes the hardware is called **Physical Design**. 

<figure>
    <img src="https://drive.google.com/uc?id=1UukCMvCLe6YCEXghL6pVpr8TOzkaYE-D" class="typical-image" />
    <figcaption>Figure 1. Circuit to Layout</figcaption>
</figure>

Actually, Physical Design contains a lot more steps to be done than the above simplified definition. Figure 1 shows the conversion of a simple transistor level circuit to a physically realizable layout. 

The [GDSII](https://en.wikipedia.org/wiki/GDSII){:target="_blank"} layout format is a binary file format that represents your IC layout using geometric shapes, text labels and additional foundry specific information in a hierarchical form. You might understand what this means by looking at the video below which shows a GDSII layout file in 3D (created by IC Design Group at University of Twente).

<div class="youtube-video-container">
  <iframe width="560" height="315" src="https://www.youtube.com/embed/F4EArOqNNSU?start=3" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

In VLSI, Physical Design is the only domain where you can see circuits in a Graphical User Interface (GUI) with geometric shapes and colors as shown in Figure 2. It is an excellent career choice for engineering minds with an *artistic* background because you will be drawing layout specific geometries either manually or using code!

<figure>
    <img src="https://drive.google.com/uc?id=13C4Wv7XlTi9WUdiC7q_EBHD1jxPjsGcD" class="typical-image" />
    <figcaption>Figure 2. A typical chip when looked from a physical design perspective</figcaption>
</figure>

By this time, you might be overwhelmed by the complexity of the layout artwork (which finally becomes your hardware IC) that you have just seen in the above video and image. But, don't worry. This is where automation becomes your friend!

Physical Design involves dedicated automation flows and methodologies for each and every step in the design process with the help of Electronic Design Automation (EDA) tools and scripts written in languages such as Tcl, Perl or Python. 

A design will never function as expected if it is not verified and validated 100% before manufacturing. Hence, Physical Design involves robust verification flows (or the so-called [signoff](https://en.wikipedia.org/wiki/Signoff_(electronic_design_automation)){:target="_blank"} flows) to verify and validate the design in terms of timing, power, area and functionality.

---

<h3 id="why-vlsi-physical-design-flow">Why VLSI Physical Design Flow?</h3>

Physical design is all about placing instances defined in the netlist and connecting them by routing through metal layer stack to satisfy design specifications such as performance, power and area (PPA). Current IC designs have *multi-million instances* that are interconnected with *several stack of metal layers* that connect these instances. Manually performing each step in the design process is not feasible, takes huge amount of time and is error prone.

The complexity in designing a multi-million instance based IC is huge and hence we need dedicated automation flows that complete specific tasks needed to be performed at each step in the design which reduces design time and errors. These flows require knowledge and understanding of [EDA tools](https://en.wikipedia.org/wiki/Electronic_design_automation){:target="_blank"} and [scripting languages](https://en.wikipedia.org/wiki/Scripting_language){:target="_blank"} such as Tcl, Perl or Python.

In addition to complexity, as time to market for chips is decreasing, reuse of IP (Intellectual Property) blocks is highly preferred in each design.

---

<h3 id="vlsi-physical-design-flow">VLSI Physical Design Flow</h3>

Typical VLSI Physical Design (PD) flow is shown in Figure 3. This is a standard flow that is followed in modern IC design. Each step in the PD flow has sub flows or further steps that are needed to be performed.

<figure>
    <img src="https://drive.google.com/uc?id=116LfKvpnRinjDT7uVDttK7q2WTqWiqh7" class="typical-image" />
    <figcaption>Figure 3. VLSI Physical Design Flow</figcaption>
</figure>

Major steps involved in Physical Design are
* Importing Inputs 
* Floorplanning & Partitioning
* Power Planning
* Placement
* Clock Tree Synthesis (CTS)
* Routing

Major verification (signoff) steps involved in Physical Design are
* Static Timing Analysis (STA)
* Power Distribution Network Analysis (PDN)
* Physical Verification (PV)
* Formal Verification (FV)
* Conformal Low Power Verification (CLP)

Commonly used EDA tools for Floorplanning, Place and Route are 
* [Cadence Innovus](https://www.cadence.com/content/cadence-www/global/en_US/home/tools/digital-design-and-signoff/hierarchical-design-and-floorplanning/innovus-implementation-system.html){:target="_blank}
* [Cadence First Encounter](https://www.cadence.com/content/cadence-www/global/en_US/home/tools/digital-design-and-signoff/block-implementation/first-encounter-design-exploration-and-prototyping.html){:target="_blank"}
* [Synopsys IC Compiler II](https://www.synopsys.com/implementation-and-signoff/physical-implementation/ic-compiler-ii.html){:target="_blank"}

Commonly used EDA tools for signoff checks are
* [Synopsys StarRC](https://www.synopsys.com/implementation-and-signoff/signoff/starrc.html){:target="_blank"} for Parasitic Extraction
* [Synopsys PrimeTime](https://www.synopsys.com/implementation-and-signoff/signoff/primetime.html){:target="_blank"} for Static Timing Analysis
* [Apache RedHawk](https://www.ansys.com/products/semiconductors/ansys-redhawk){:target="_blank"} for Power Analysis and Debugging
* [Mentor Graphics Calibre](https://www.mentor.com/training/course_categories/calibre){:target="_blank"} for Physical Verification
* [Cadence Logic Equivalence Checker](https://www.cadence.com/content/cadence-www/global/en_US/home/tools/digital-design-and-signoff/logic-equivalence-checking.html){:target="_blank"} for Formal Verfication
* [Cadence Conformal Low Power](https://www.cadence.com/content/cadence-www/global/en_US/home/tools/digital-design-and-signoff/low-power-validation/conformal-low-power.html){:target="_blank"} for Conformal Low Power Verification

---

<h3 id="importing-inputs">Importing Inputs</h3>

<div class="note">
  <p><b>Goal</b>: Gather all the required inputs for physical design such as gate level netlist <span class="coding">.v</span> / <span class="coding">.vhdl</span>, Technology file <span class="coding">.tech</span>, UPF (Unified Power Format) files <span class="coding">.upf</span>, Library files that include LIBs <span class="coding">.lib</span>, LEFs <span class="coding">.lef</span>, DEFs <span class="coding">.def</span> and GDS <span class="coding">.gds</span> of standard cells and IPs and SDC (Synopsys Design Constraint) files <span class="coding">.sdc</span>. </p>
</div>

Inputs to physical design are the most important files that you will need to start your design process. If the inputs are read in the EDA tools without any issues (warnings and errors), then your physical design flow goes smooth.

Commonly required inputs to start physical design for an IC are 
* Gate-level Netlist <span class="coding">.v</span> or <span class="coding">.vhdl</span> (given by synthesis people)
* Technology file <span class="coding">.tech</span> (given by fabrication people)
* Logical libraries <span class="coding">.lib</span> (given by vendors)
* Physical libraries <span class="coding">.lef</span> <span class="coding">.def</span> <span class="coding">.gds</span> (given by vendors)
* UPF (Unified Power Format) files <span class="coding">.upf</span> (given by UPF people)
* SDC (Synopsys Design Constraints) files <span class="coding">.sdc</span> (given by synthesis people) 

---

<h3 id="floorplanning-and-partitioning">Floorplanning & Partitioning</h3>

<i>Related Terminologies: [<a href="https://gogul09.github.io/hardware/physical-design-terminologies#floorplanning" target="_blank">Floorplanning</a>]</i>

<div class="note">
  <p><b>Goal</b>: Calculate the die size, create IO ring, partition the design and calculate the size, shape and placement of partitions (HMs or blocks), figure out the position of custom macros such as analog macros and create PG grid.</p>
</div>

In today's IC design, because of huge design complexity, hierarchical design approach is followed. What this means is, the entire chip is divided into partitions or blocks that are interconnected at a <span class="coding">TOP_LEVEL</span> module.

Figure 4 shows a typical <span class="coding">TOP_LEVEL</span> floorplan module of an IC with abutted blocks, non-abutted blocks and routing channels.

<figure>
    <img src="https://drive.google.com/uc?id=1FgocjfTQNYG5MJF8g17_WQzb-3ss1aBG" class="typical-image" />
    <figcaption>Figure 4. A typical view of top-level floorplan of an IC</figcaption>
</figure>

This <span class="coding">TOP_LEVEL</span> module of your chip contains hard blocks and soft blocks with or without glue logic (standard cells in <span class="coding">TOP_LEVEL</span>).
* **Hard** blocks are those sub-blocks whose shapes *cannot* be changed. These blocks are mostly IPs or <a href="https://gogul09.github.io/hardware/physical-design-terminologies#macro" target="_blank">macros</a> that are already designed and validated for that particular [technology node](https://en.wikichip.org/wiki/technology_node){:target="_blank"}. Placement of these blocks are decided based on design understanding and package requirements in <span class="coding">TOP_LEVEL</span>.
* **Soft** blocks are those blocks whose shapes *can* be changed to meet predefined cost metrics such as chip area, wirelength and wire congestion. These are the blocks that are needed to be designed and validated for chip-level convergence. In industry terms, these **soft** blocks are called as **Hard Macros** or **HMs**.

During floorplanning, one must ensure proper shapes for the hard macros (HMs) until convergence is reached in terms of cost metrics, timing, power and area.

Due to design complexity and runtime of EDA tools, each hard macro (HM) is created using the same design steps such as floorplanning, placement and routing and then integrated at the <span class="coding">TOP_LEVEL</span> module.

Dividing the entire design into smaller sub-designs (partitions) makes design convergence easier. This is because, the runtime of EDA tools for a single partition (block) will take lesser time for each step in the PD flow when compared to entire design.

Physical Design is all about tradeoffs between **area**, **speed** and **power**. Thus, floorplanning is a *highly iterative process* which takes into account the hard blocks and soft blocks used, memories, IO pads and their placement in the design, routing possibilities between different blocks and inside the blocks, power grid structure for each macro and cell in the design, and also the aspect ratio and IO structure of the entire design.

---

<h3 id="power-planning">Power Planning</h3>

<i>Related Terminologies: [<a href="https://gogul09.github.io/hardware/physical-design-terminologies#power-distribution" target="_blank">Power Distribution</a>]</i>

<div class="note">
  <p><b>Goal</b>: Decide on power dissipation number and construct power distribution network accordingly to power up blocks, IO pads, macros and standard cells.</p>
</div>

<span class="coding">VDD</span> and <span class="coding">VSS</span> that you see in the transistor level circuit in Figure 1 needs to be supplied to every transistor in a multi-million transistor design. Thus, power from a single battery source must be delivered to each cell in the design. To accomplish this, power planning is done.

During floorplanning, power planning is a step that is done to construct the power distribution network to supply power to all blocks, macros and standard cells equally.

<figure>
    <img src="https://drive.google.com/uc?id=1ECjeWM7ftyeFnILkx4IPcm6sQDtPPlCT" class="typical-image" />
    <figcaption>Figure 6. Power Planning (or Power Distribution) in an IC</figcaption>
</figure>

As shown in Figure 6, there are two types of power distribution strategies followed in chip design namely Wire Bonding and Flip-Chip [(read more)](https://gogul09.github.io/hardware/low-power-vlsi-design-basics-1){:target="_blank"}. Using any one of these two power distribution strategies, we usually form power rings, stripes and rails through out the design.

1. **Rings** - Supplies <span class="coding">VDD</span> and <span class="coding">VSS</span> around the chip.
2. **Stripes** - Supplies <span class="coding">VDD</span> and <span class="coding">VSS</span> across/throughout the chip.
3. **Rails** - Supplies <span class="coding">VDD</span> and <span class="coding">VSS</span> to the standard cells in the design.

Main steps to be taken care during power planning are
* Decision on width, pitch and offset of power stripes for each metal layer.
* Block power hook up at <span class="coding">TOP_LEVEL</span>.
* IO power hook up at <span class="coding">TOP_LEVEL</span>.
* Standard cells power hook up inside block as well as <span class="coding">TOP_LEVEL</span>.
* Shorts and Opens are to be checked and fixed.

---

<h3 id="placement">Placement</h3>

<i>Related Terminologies: [<a href="https://gogul09.github.io/hardware/physical-design-terminologies#placement" target="_blank">Placement</a>]</i>

<div class="note">
  <p><b>Goal:</b> Place all the standard cells in the design to minimize total area, reduce interconnect cost, reduce congestion hotspots and improve timing. </p>
</div>

After floorplanning the design, for each block, [standard cells](https://en.wikipedia.org/wiki/Standard_cell){:target="_blank"} are placed inside the block. These standard cells are the functional cells that contain the necessary logic functionality for your chip that are provided to you by the [foundry](https://en.wikipedia.org/wiki/Semiconductor_fabrication_plant){:target="_blank"}. Inside the standard cells, you could find the individual transistors that make up the logic functionality. *Ex: AND gate, OR gate, 2x1 multiplexer etc.*

> If you think of a **chip** as the **house**, then **placement** is the process of placing **each individual brick** (standard cell) that make up the house.

In a multi-million instances design, placing these cells manually is not feasible. Hence, EDA tool place these cells in the standard cell rows (created during floorplanning) with conflicting goals of optimizing congestion, timing and power. Placement is carried out with the help of virtual route.

Virtual route is a rough estimate for the EDA tool to measure the shortest [manhattan distance](https://www.quora.com/What-is-Manhattan-Distance){:target="_blank"} from one standard cell pin to another. Based on this distance, timing is calculated roughly and these cells are placed accordingly.

A good placement reduces the delay of interconnect wires, has shorter interconnect wire length and has lesser congestion hotspots. One key thing performed during placement is **legalization** which means placing standard cells at appropriate locations without any placement constraint violation or design rule violation. Placement greatly determines the routability of the design.

Standard placement flow involves the following steps.
* Pre-placement
* Global placement
* High Fanout Net (HFN) synthesis
* Scan Chain Reordering
* Detail Placement
* Timing Optimization
* Leakage/Area Recovery
* Legalization

---

<h3 id="clock-tree-synthesis">Clock Tree Synthesis</h3>

<i>Related Terminologies: [<a href="https://gogul09.github.io/hardware/physical-design-terminologies#clock-tree-synthesis" target="_blank">Clock Tree Synthesis</a>]</i>

<div class="note">
  <p><b>Goal:</b> Minimize skew, latency and insertion delay for clock signals reaching all the sequential elements in the design.</p>
</div>

Clock is an important component in digital design as sequential circuits such as flipflops and registers require clock signal to function properly. Before clock tree synthesis, the clock is considered as <span class="coding">ideal</span> i.e. right from the source it travels to all the clock pins (sinks) without any delay. But after CTS, the clock is <span class="coding">propagated</span> which means there is considerable amount of delay involved between the clock signal entering one flipflop and another flipflop in the design which is defined as [clock skew](https://en.wikipedia.org/wiki/Clock_skew){:target="_blank"}.

The goal of clock tree synthesis is to reduce this clock skew, balance it and minimize insertion delay (propagation delay from clock source to sink). This is done with the help of constructing a clock tree using special cells such as *clock tree inverters* to maintain exact duty cycle (transition) and *clock tree buffers* to balance the skew and latency involved.

> At fast speeds or long distances, because of **clock skew** serial interfaces (ex: USB) are preferred over parallel interfaces (ex: parallel SCSI).

Additionally, these clock tree inverters and buffers should be added carefully with area and power constraints in mind. Commonly used clock trees are *H-Tree, Fishbone Tree and Star Tree*.

Main steps to be taken care during CTS are
* Target minimum possible clock skew.
* Target minimum possible latency.
* Max transition and Max capacitance limits must be met.
* Apply Non-Default Routing (NDR) rules for clock nets to reduce crosstalk and noise (signal integrity).

---

<h3 id="routing">Routing</h3>

<i>Related Terminologies: [<a href="https://gogul09.github.io/hardware/physical-design-terminologies#routing" target="_blank">Routing</a>]</i>

<div class="note">
  <p><b>Goal:</b> Physically connect all the interconnects (nets) in the design with physical constraints such as DRC, wire length, timing, noise and crosstalk to be taken care.</p>
</div>

After placing all the standard cells in the design, interconnects (nets) must be routed physically using the metal layer stack with wires and vias. Routing is typically done in two steps.

1. **Global Routing** - Generate a rough route (routing region, track assignment) for each net in the design without specifying the actual layout of wires (loosely routed).
2. **Detail Routing** - Generate actual geometry layout for each net in the design using different metal layers.

Each metal layer in the metal layer stack of your design has *preferred routing direction* as well as *non-preferred routing direction*. For example, <span class="coding">M2</span> metal layer might have preferred routing direction as *horizontal* and non-preferred routing direction as *vertical*. This constraint is based on the technology node rule.

Main steps to be taken care during routing are
* Wire length must be minimized.
* Congestion hotspots must be reduced.
* Noise & Crosstalk must be reduced using shielding and/or NDR techniques.
* DRC rules (geometry rules) must be honored during detail routing.
* Shorts must be very minimal.

---

<h3 id="static-timing-analysis">Static Timing Analysis</h3>

<i>Related Terminologies: [<a href="https://gogul09.github.io/hardware/physical-design-terminologies#static-timing-analysis" target="_blank">Static Timing Analysis</a>]</i>

<div class="note">
  <p><b>Goal:</b> Validate the design with respect to timing and verify whether the design could operate at the specified clock frequency without any timing violations such as setup, hold, recovery, removal, max transition and max capacitance across different <a href="https://en.wikipedia.org/wiki/Process_corners" target="_blank">PVT corners</a>.</p>
</div>

Once the design is placed and routed, it is validated for timing. STA involves checking whether the design meets the *specified clock frequency* and is free of *timing violations* such as setup, hold, recovery, removal, maximum transition, maximum capacitance etc., across different *PVT corners* or *operating conditions*.

STA largely depends on [parasitic extraction](https://en.wikipedia.org/wiki/Parasitic_extraction){:target="_blank"} which is a process of extracting the R (resistance) and C (capacitance) of the interconnect metal traces in the design which are obtained only after detail routing. These RC parasitics causes propagation delay that is further added by the gate delay, resulting in timing degradation.

You can read more about Static Timing Analysis in the below links.

* [STA Timing Paths and Delays](https://gogul09.github.io/hardware/sta-timing-paths-and-delays){:target="_blank"}
* [STA CMOS Basics (Part 2)](https://gogul09.github.io/hardware/cmos-basics-for-sta-2){:target="_blank"}
* [STA CMOS Basics (Part 1)](https://gogul09.github.io/hardware/cmos-basics-for-sta-1){:target="_blank"}
* [STA MOSFET fundamentals](https://gogul09.github.io/hardware/mosfet-fundamentals){:target="_blank"}

---

<h3 id="power-verification">Power Verification</h3>

<i>Related Terminologies: [<a href="https://gogul09.github.io/hardware/physical-design-terminologies#power-verification" target="_blank">Power Verification</a>]</i>

<div class="note">
  <p><b>Goal:</b> Validate the design with respect to power and verify whether the design meets static and dynamic IR drop thresholds, and is free from electromagnetic effects.</p>
</div>

Similar to timing validation, power analysis and debugging is done to ensure that the design is free from power related issues such as static IR drop, dynamic IR drop and electromagnetic issues.

Only if the design meets power numbers specified in the design specifications, it can last longer. Hence, power is a primary concern for chip designers due to decreasing technology node and increasing metal layer stack.

You can read more about low power design in the below links. 
* [Low Power VLSI Design Basics (Part 1)](https://gogul09.github.io/hardware/low-power-vlsi-design-basics-1){:target="_blank"} 
* [Low Power VLSI Design Basics (Part 2)](https://gogul09.github.io/hardware/low-power-vlsi-design-basics-2){:target="_blank"}.

---

<h3 id="physical-verification">Physical Verification</h3>

<i>Related Terminologies: [<a href="https://gogul09.github.io/hardware/physical-design-terminologies#physical-verification" target="_blank">Physical Verification</a>]</i>

<div class="note">
  <p><b>Goal:</b> Validate the design layout with respect to physical geometries and technology rules for electrical correctness, logical correctness and manufacturability, and make sure the design passes DRC, LVS, ERC, Antenna check and XOR check.</p>
</div>

This is the final signoff check that is done for your design before you tape-out your design for fabrication. Design must have zero shorts, zero opens, zero design rule violation, zero antenna violation, zero base violation and must be logically equivalent as the synthesized logic netlist.

You can read more about physical verification checks [here](https://en.wikipedia.org/wiki/Physical_verification){:target="_blank"}.

<h3 id="references">References</h3>

1. [Routability-Driven Bump Assignment for Chip-Package Co-Design](http://www.aspdac.com/aspdac2014/technical_program/pdf/6B-3.pdf){:target="_blank"}