---
layout: post
category: hardware
class: PD Concepts
title: Physical Design - Terminologies
description: In VLSI Physical Design, there are lots of terminologies involved. In this page, you will find the description of mostly used terminologies which might be helpful for beginners.
author: Gogul Ilango
permalink: /hardware/physical-design-terminologies
image: https://drive.google.com/uc?id=1UoyhfdcF_Aj-NBU8WNzGz83SRp5Zhg3L
cardimage: https://drive.google.com/uc?id=13C4Wv7XlTi9WUdiC7q_EBHD1jxPjsGcD
---

<div class="sidebar_tracker" id="sidebar_tracker">
  <button onclick="closeSidebar('sidebar_tracker_content')">X</button>
  <p onclick="showSidebar('sidebar_tracker_content')">Contents</p>
  <ul id="sidebar_tracker_content">
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_1" href="#floorplanning">Floorplanning</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_2" href="#placement">Placement</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_3" href="#routing">Routing</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_4" href="#power-distribution">Power Distribution</a></li>
    <li><a class="sidebar_links" onclick="handleSideBarLinks(this.id)" id="link_4" href="#physical-verification">Physical Verification</a></li>
  </ul>
</div>

In Physical Design (PD), there are so many terminologies involved. It could be daunting for a fresher to get acquainted with these terms at the beginning of his career. So, I thought of making a page with terminologies and its description. It might be helpful for a beginner or an experienced professional to quickly refer something related to PD.

I will be regularly updating this page if I found some new terminology along with its description. Make sure you bookmark it. 😉

<div class="math-cover">
	<h3><a href="#floorplanning">Floorplanning</a></h3>
	<div class="toc-box">
		<ul>
			<li><a href="#aspect-ratio">Aspect Ratio</a></li>
			<li><a href="#cell-orientation">Cell Orientation</a></li>
			<li><a href="#core-boundary">Core Boundary</a></li>
			<li><a href="#core-utilization">Core Utilization</a></li>
			<li><a href="#flylines">Flylines</a></li>
			<li><a href="#halo">Halo</a></li>
			<li><a href="#instance">Instance</a></li>
			<li><a href="#macro">Macro</a></li>
			<li><a href="#manufacturing-grid">Manufacturing Grid</a></li>
			<li><a href="#net">Net</a></li>
			<li><a href="#physical-cells">Physical Cells</a></li>
			<li><a href="#pin">Pin</a></li>
			<li><a href="#placement-blockage">Placement Blockage</a></li>
			<li><a href="#placement-grid">Placement Grid</a></li>
			<li><a href="#port">Port</a></li>
			<li><a href="#power-domain">Power Domain</a></li>
			<li><a href="#row">Row</a></li>
			<li><a href="#routing-blockage">Routing Blockage</a></li>
			<li><a href="#track">Track</a></li>
			<li><a href="#voltage-island">Voltage Island</a></li>
			<li><a href="#wire">Wire</a></li>
		</ul>
	</div>
	<br>
	<h3><a href="#placement">Placement</a></h3>
	<div class="toc-box">
		<ul>
			<li><a href="#cell-legalization">Cell Legalization</a></li>
			<li><a href="#cell-padding">Cell Padding</a></li>
			<li><a href="#driver">Driver</a></li>
			<li><a href="#fanin">Fanin</a></li>
			<li><a href="#fanout">Fanout</a></li>
			<li><a href="#load">Load</a></li>
			<li><a href="#placement-density">Placement Density</a></li>
			<li><a href="#standard-cells">Standard Cell</a></li>
		</ul>
	</div>
	<br>
	<h3><a href="#routing">Routing</a></h3>
	<div class="toc-box">
		<ul>
			<li><a href="#congestion">Congestion</a></li>
			<li><a href="#detail-routing">Detail Routing</a></li>
			<li><a href="#global-routing">Global Routing</a></li>
			<li><a href="#metal-layers">Metal Layers</a></li>
			<li><a href="#ndr">NDR</a></li>
			<li><a href="#via">VIA</a></li>
		</ul>
	</div>
	<br>
	<h3><a href="#power-distribution">Power Distribution</a></h3>
	<div class="toc-box">
		<ul>
			<li><a href="#pmic">PMIC</a></li>
			<li><a href="#gridcheck">Gridcheck</a></li>
			<li><a href="#static-ir-drop">Static IR Drop</a></li>
			<li><a href="#dynamic-ir-drop">Dynamic IR Drop</a></li>
			<li><a href="#esd-cell">ESD Cell</a></li>
		</ul>
	</div>
	<br>
	<h3><a href="#physical-verification">Physical Verification</a></h3>
	<div class="toc-box">
		<ul>
			<li><a href="#antenna">Antenna</a></li>
			<li><a href="#drc">DRC</a></li>
			<li><a href="#erc">ERC</a></li>
			<li><a href="#lvs">LVS</a></li>
			<li><a href="#shorts">Shorts</a></li>
		</ul>
	</div>
</div>

<h3 class="centered-heading" id="floorplanning"><span>Floorplanning</span></h3>

* <p class= "para-heading" id="aspect-ratio">Aspect Ratio</p>
It is the ratio between height and width of the core or a block. Routing resources, congestion, placement of standard cells, timing, clock-tree, placement of IO pads and packaging depends on the aspect ratio of the core or a block.

<div class="math-cover">
$$
aspect\;ratio = \frac{height\;of\;the\;core}{width\;of\;the\;core}
$$
</div>

* <p class= "para-heading" id="cell-orientation">Cell Orientation</p>
Every instance in a design such as a block, a macro, an IO pad or a standard cell have orientation associated with them. Orientation is defined as the rotation and/or mirroring of that instance about x or y axis to make connections meaningful and easier. Different types of cell orientations are R0, MX, MY, R90, R180, R270, MX90, MY90.
  * <span class="coding">R0</span> - No rotation.
  * <span class="coding">MX</span> - Mirror through x-axis.
  * <span class="coding">MY</span> - Mirror through y-axis.
  * <span class="coding">R90</span> - Rotate 90 degrees counter-clockwise.
  * <span class="coding">R180</span> - Rotate 180 degrees counter-clockwise.
  * <span class="coding">R270</span> - Rotate 270 degrees counter-clockwise.
  * <span class="coding">MX90</span> - Mirror through x-axis and rotate 90 degrees counter-clockwise.
  * <span class="coding">MY90</span> - Mirror through y-axis and rotate 90 degrees counter-clockwise.

* <p class= "para-heading" id="core-boundary">Core Boundary</p>
It is the area or region within which standard cells and macros are placed in the design. From top-level of a design, core boundary will be rectangular or square shaped. From block-level of a design, core boundary may have rectangular or rectilinear shape.

* <p class= "para-heading" id="core-utilization">Core Utilization</p>
It defines the total area occupied by the standard cells and macros in the block or top-level design. Typically, 70-80% utilization is taken into account for blocks as timing optimization involves placement of buffers or inverters which requires area.

<div class="math-cover">
$$
core\;utilization = \frac{standard\;cell\;area\;\;+\;macro\;cells\;area}{total\;core\;area}
$$
</div>

* <p class= "para-heading" id="flylines">Flylines</p>
These are virtual lines that shows logical connections from an instance (block or macro or cell or IO pad). Using flylines, one can understand different connections from a block or a macro or a cell or an IO pad with which floorplanning could be done easily.

* <p class= "para-heading" id="halo">Halo</p>
It is the area around the boundary of a block or a macro or a standard cell within which no other block or standard cell or macro is placed. If the blocks or standard cells or macros are moved, halos for those instances move along with it. It is also called as the *keepout region*. Halos of two adjacent instances can be overlapped.

* <p class= "para-heading" id="instance">Instance</p>
A single occurance or a single object of a standard cell type or a macro or a block defined with a unique instance name. *Ex: a 2-input AND gate could be instantiated as <span class="coding">CELL_AND_1</span> and a usb 2.0 macro could be instantiated as <span class="coding">USB_2_0_1</span>.* 

* <p class= "para-heading" id="macro">Macro</p>
A Macro is an Intellectual Property (IP) in a design that is owned by a company. These are reusable logic blocks used in a design without the necessity of building them from scratch. Two types of macro are Soft Macro and Hard Macro. 
  * *Soft Macro* is not specific to any technology node. Due to this, soft macros are unpredictable in terms of timing, area and power. But soft macros are more flexible in terms of reconfigurability and can be modified at the RTL level.
  * *Hard Macro* is what we call as a *Block* in PD. It is designed specific to a technology node to meet timing, area and power. 

* <p class= "para-heading" id="manufacturing-grid">Manufacturing Grid</p>
The smallest resolution of the technology node is called as the Manufacturing Grid. Any geometry (or shape) created in the design must be snapped (or aligned) with this grid to avoid DRC errors.

* <p class= "para-heading" id="net">Net</p>
A logical connection between two or more pins of different instances. Some of the different types of net in a design are single fanout net, multi-fanout net, power net, ground net, signal net, clock net etc.

* <p class= "para-heading" id="physical-cells">Physical Cells</p>
These cells do not have any logical functionality in the design. Some of the standard physical cells are tap cells, tie cells, endcap cells, decap cells, filler cells, spare cells. 

* <p class= "para-heading" id="pin">Pin</p>
A pin is an IO terminal that is present in blocks or hard-macros or standard-cells of a design. *Ex: For a 2-input AND gate, <span class="coding">CELL_AND_1/a</span>, <span class="coding">CELL_AND_1/b</span> are the input pins and <span class="coding">CELL_AND_1/z</span> is the output pin.*

* <p class= "para-heading" id="placement-blockage">Placement Blockage</p>
It is the area defined by the designer for the PnR tool to avoid placing, legalizing or overlapping standard cells in that particular area. If a block or standard cell or macro or IO pad is moved, placement blockages does not move along with it.
  * *Hard placement blockage* means that the tool must not place, legalize or overlap any standard cell (including buffers and inverters) in the mentioned blockage area.
  * *Non-buffer blockage* means that the tool can place, legalize or overlap any buffer or inverter in the mentioned blockage area except other standard cells in the design.
  * *Partial blockage* means that the designer can adjust the percentage of blockage inside the blockage area and the tool should honor it. By default, 100% placement is blocked inside the blockage area.

* <p class= "para-heading" id="placement-grid">Placement Grid</p>
Placement grid is a multiple of the manufacturing grid in which all the standard cells are placed. Based on the placement grid, rows are formed and standard cells are placed.

* <p class= "para-heading" id="port">Port</p>
A port is an IO (Input/Output) terminal that is present in blocks or hard-macros of a design. From top-level, ports are pins in hard-macros or blocks. But from block-level, pins talking to top-level are celled as ports. Direction of ports can be input, output or in-out.

* <p class= "para-heading" id="power-domain">Power Domain</p>
It is the collection of instances or blocks that share the same supply voltage in a design. Each power domain has a separate library associated with it.

* <p class= "para-heading" id="routing-blockage">Routing Blockage</p>
It is the area defined by the designer for the PnR tool to block routing resources in single or multiple metal layers at a particular area. Routing blockages can be created and removed at any point in the design based on the requirements. It is possible to create routing blockages over a block or an instance using it's cell type or instance name without the area numbers. 

* <p class= "para-heading" id="row">Row</p>
Standard cell row is the area defined for placing standard cells in the design. Every standard cell in the design sits on the standard cell row. The row height is based on the standard cell height used in the design. Different types of rows are possible in a design based on sites or heights of standard cells used. 

* <p class= "para-heading" id="track">Track</p>
Track is a virtual line (guideline) for the PnR tool in which routing of metal wires happen in the design. For each metal layer in the design, tracks are defined for preferred and non-preferred direction with specific pitch and offset. The PnR tool routes the metal wires by assuming the track at the center of metal piece. 

* <p class= "para-heading" id="voltage-island">Voltage Island</p>
It is a dedicated area in the design which has its own row, site, cells and power structure defined for better power consumption. Level-shifters are used to convert from one voltage level to another. 

* <p class= "para-heading" id="wire">Wire</p>
A physically realized connection of a net which is routed by the router by having the center of metal piece in the track (on-track) using same or different metal layers and vias.





<h3 class="centered-heading" id="placement"><span>Placement</span></h3>

* <p class= "para-heading" id="cell-legalization">Cell Legalization</p>
It means all standard cells must be placed on the standard cell rows (in placement grid) without any off-grid violations and overlaps. Only if all cells are legalized, the PnR tool will proceed with routing. 

* <p class= "para-heading" id="cell-padding">Cell Padding</p>
It is a variable assigned to all standard cells or specific standard cell instances that belong to a cell-type in the design. Using this variable, the cell instances will have a padding associated with it around which other cells or blocks wont be placed. It's like a breathing-space for a cell which is used to avoid congestion.

* <p class= "para-heading" id="driver">Driver</p>
Any pin (or output pin) that drives one or multiple pins is called as a driver pin and it's corresponding instance is called as the driver. There can always be only one driver pin in a design. 

* <p class= "para-heading" id="fanin">Fanin</p>
The maximum number of inputs that a standard cell (or a logic gate) can accept is termed as the fanin of that standard cell.

* <p class= "para-heading" id="fanout">Fanout</p>
The maximum number of inputs (loads) that the output of a single standard cell (driver) can drive is termed as the fanout of that standard cell.

* <p class= "para-heading" id="load">Load</p>
Any pin (or input pin) that acts as a load for a driver pin is called as a load pin. There can be one or more load pins for a single driver pin, hence the term *multi-fanout*.

* <p class= "para-heading" id="placement-density">Placement Density</p>
It is the amount of area utilized for placing cells (except filler cells) in the design. There is a golden equation that this placement density should be lesser than or equal to 70% so that the remaining 30% can be used for routing resources. 

* <p class= "para-heading" id="standard-cells">Standard Cells</p>
Any complex chip is built using basic building blocks in digital design such as <span class="coding">and</span>, <span class="coding">or</span>, <span class="coding">not</span>, <span class="coding">nor</span>, <span class="coding">nand</span>, <span class="coding">flipflop</span>, <span class="coding">buffer</span> etc. Based on a technology node, these building blocks (called standard cells) are predesigned (i.e will have logical, symbol, abstract, layout and schematic views plus timing information for different scenarios) and given to the IC designer. Standard cells have fixed height and variable width. Height of these cells are same as the height of a standard cell row. In some cases, there might be double-height or triple-height cells that occupies two or three rows respectively.




<h3 class="centered-heading" id="routing"><span>Routing</span></h3>

* <p class= "para-heading" id="congestion">Congestion</p>
If the number of available routing tracks for routing in a particular area is lesser than the number of required routing tracks, then that particular area is said to be congested. Congestion creates shorts and DRCs which makes functionality fail in a design. 

* <p class= "para-heading" id="detail-routing">Detailed Routing</p>
Detail routing determines the exact physical routing for all the logical nets in the design with the help of track assignment, wires and vias insertion at different metal layers. Real picture of congestion, metal DRCs and crosstalk issues are known only after detail routing the design. 

* <p class= "para-heading" id="global-routing">Global Routing</p>
Global routing partitions the entire design into tiles or global routing cells or g-cells and then, the paths for various nets are computed. Global routing doesn't necessarily assign specific tracks to each net, but assigns each net to specific g-cells. Congestion can be estimated earlier in the design using Global routing before starting detail routing.

* <p class= "para-heading" id="metal-layers">Metal Layers</p>
Based on technology node, there are different metal layers involved for routing. Each metal layer is designated with a name say M1 or M3 and each metal layer has preferred and non-preferred directions with well-defined width, pitch, offset and tracks. *Ex: M1 can have preferred direction as vertical and non-preferred direction as horizontal, while M4 can have preferred direction as horizontal and non-preferred direction as vertical.*

* <p class= "para-heading" id="ndr">NDR</p>
Non-Default Rule is a routing rule applied for a single net or a group of nets that is not default. Default routing rule have defined width and spacing for each metal layer and via. Using Non-Default Rules, one can create an NDR rule with double or triple the width with double or triple the spacing. *Ex: 1W2S means single width and twice the default spacing*. NDRs are used for clock nets and critical nets (high-frequency nets) in a design to avoid Signal Integrity (SI) issues such as crosstalk and noise. 

* <p class= "para-heading" id="shorts">Shorts</p>
When two or more wires or vias of different nets in the same metal layer cross each other, then it is termed as a short. Shorts are the number one concern after detail routing a block. These overlapping wire segments must be corrected for proper functioning of the design. 

* <p class= "para-heading" id="via">VIA</p>
Vertical Interconnect Access (VIA) is the small vertical path (or opening) in an insulating oxide layer (cut-layer) that allows a conductive path (or connection) between different metal layers. Some types of VIA are single VIA, stacked VIA, VIA array etc.



<h3 class="centered-heading" id="power-distribution"><span>Power Distribution</span></h3>

* <p class= "para-heading" id="pmic">PMIC</p>
PMIC or Power Management Integrated Circuit takes care of all possible supported external supplies and defines the power sequence for the board. It supplies power to different components inside the board. Also, it protects the board from unsupported overvoltage and undervoltage. It is usually software-controllable (often as an I2C device). Different voltage values such as VDD_1, VDD_2, VDD_3 etc., inside a chip are obtained using a PMIC.

* <p class= "para-heading" id="gridcheck">Gridcheck</p>
Gridcheck is a verification process that is performed to check for opens and shorts in the power distribution grid of a design. For a design to function properly, it must be free from opens and shorts. Before analyzing a design for static and dynamic IR drop, it must be free from opens and shorts (i.e. zero opens and zero shorts).

* <p class= "para-heading" id="static-ir-drop">Static IR Drop</p>
As the name suggests, even when the chip is off or quiescent (static), there exists some amount of power dissipation due to transistor's leakage characteristics giving rise to leakage power. This is due to the characteristic of CMOS transistors itself, which is a function of power supply voltage \\( V_{DD} \\), threshold voltage \\( V_{th} \\) and transistor's dimension (width \\(W \\) and length \\( L \\)). Static IR drop analysis is a  vectorless IR drop analysis with average current cycles. It is typically used for Electro-Migration (EM) analysis where current limit is checked for wires.

* <p class= "para-heading" id="dynamic-ir-drop">Dynamic IR Drop</p>
As the name suggests, dynamic power dissipation occurs when the transistors are switching from one logic state to another. There are two types of dynamic power dissipation in CMOS circuits namely switching power and short-circuit power. Dynamic IR drop analysis is a vectorless or VCD based IR drop analysis with worst-case switching currents. It is typically used to check voltage drop limit for switching instances.

* <p class= "para-heading" id="esd-cell">ESD Cell</p>
ESD or Electro-Static Discharge cells are clamp circuits that are placed at appropriate locations in the chip to provide a low impedance discharge path for the Electro-Static Discharge and clamp the signal voltage at a level that avoids dielectic breakdown. As technology node decreases in feature size, ESD cells are mandatory to avoid functional failure or burn out of the chip.

<h3 class="centered-heading" id="physical-verification"><span>Physical Verification</span></h3>

* <p class= "para-heading" id="antenna">Antenna</p>
Antenna violation, commonly referred as the plasma induced gate oxide damage, occurs during manufacturing stage of a chip. It is a result of charge accumulation on metals and discharge to a transistor's gate through gate oxide which ultimately damages the gate.

* <p class= "para-heading" id="drc">DRC</p>
Design Rule Checks are performed at the physical design stage to verify if the designed layout meets the design rules so that the design can be manufactured properly without any issues. These design rules are specific to a technology node and are provided to the designer by the foundry. Base and Metal are checked and verified completely with zero DRC error before tapeout. DRC include physical layout checks such as metal width, metal pitch, metal spacing, via spacing, via type, base (well connectivity).

* <p class= "para-heading" id="lvs">LVS</p>
Layout vs Schematic is another physical verification check that is performed at the physical design stage. This is to ensure that the designed layout is functionally the same as the schematic netlist so that there isn't any deviation in functionality of the design. There must be zero opens and shorts without any DRC errors. Some other LVS errors are parameter mismatches and unbound pins.

* <p class= "para-heading" id="erc">ERC</p>
Electrical Rule Check is a physical verification check that reports any electrical connection that is potentially dangerous. It checks the design for accurate power and ground connections. Transistors with gate unconnected (floating gate), wrong transistor-level connections (such as shorted drain and source, connecting high voltage to thin gates), floating nets, floating pins, floating wells, antenna errors are some of the checks reported here.