# put_on_edge
This is an open standard for PCB edge connector pinning of various interfaces. It uses the AVX Corporation 009159010061916 connector (or lower pin variants) which is low cost, high density and most importantly needs no soldering and is not permanently attached to a PCB. 

Its important to note that the manufacturers pinning scheme is not used, rather the pinning scheme from the DebugEdge project:

![](pinning.png)

Rational for the pinning scheme change is that narrower connectors share common pin names relative to the orientation notch. 

# naming and labeling
In order to uniquely identify which standard an edge connector adhears to it is suggested to use the foillowing naming convention: 
[organization letter code].[interface number code].[optional subversion]

**example** osf.12.0

Rational for this scheme is that there is minimal space on the PCB yet each interface should be uniquely identified. In order for other organizations or hobbiests to make their own extentions the organization identification is needed.


## global conventions
Each interface in the respective subfolders will define its own pinning. However there are a few conventions which every interface connector should conform to.

### host/device
There are two seperate footprints for host/device side. For many interfaces it is clear which is which. On designs it will be noted which side is host and which is device.

### spacing
In order to allow for standard 13mm wide adapter boards connectors should be placed no closer than 16mm apeart on a board edge (measured pin 1 to pin 1 reguardless of connector pin count). 

### GND
Pin 1 is always GND.

### orientation
Pin 1 should always be on the top side of the board, this will make reverse connections less common.

Host connectors should generally be oriented on the right or bottom side of a board and device connectors on the left or top. 

### galvanic isolation friendly pinning
Galvanic isolation modules (such and the iCoupler series) can support many different interfaces with one generic isolator. Care should be taken to standardize the interface such that a generic isolation device can be used for several different interface (SPI and UART for example). 
| Pin | Description |
| --- | ----------- |
| 1 | GND |
| 2 | host out|
| 3 | host in|
| 4 | host out|
| 5 | host in|
| 6 | host out|
| 7 | host in|
| 8 | host out|
| 9 | 3.3V |
| 10 | 5V | 
