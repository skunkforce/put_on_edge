# put_on_edge
This is an open standard for PCB edge connector pinning of various interfaces. It uses the AVX Corporation [009159010061916](https://datasheets.kyocera-avx.com/OpenEndedCardEdge_00-9159.pdf) connector which is low cost, high density and most importantly needs no soldering and is not permanently attached to a PCB. 
![](doc/card_edge_connector.png)

## why standardize board to board connections?
A lot of effort is lost on documenting the pinout of connectors while prototyping as well as fiddling with zumper wire connectors. This project is an effort to reduce that effort as most interfaces are pretty well defined already. 
For a motivating example see [the edgy boards project]() or think of a decomposed circuit prototype with defined interfaces between the compoinents such as ![](doc/motivating_example.drawio.png). 

# naming and labeling
In order to uniquely identify which standard an edge connector adhears to it is suggested to use the foillowing naming convention: 
[organization letter code].[interface number code].v[optional subversion]

**example** osf.012.v0.1

Rational for this scheme is that there is minimal space on the PCB yet each interface should be uniquely identified. In order for other organizations or hobbiests to make their own extentions the organization identification is needed.


## global conventions
Each interface in the respective subfolders will define its own pinning. However there are a few conventions which every interface connector should conform to.

### host/device
There are two seperate footprints for host/device side. For many interfaces it is clear which is which. Small arows on the top silkscreen help visually identify which side is host and which is device. Host connectors are usually placed on the right side of the board and device side connectors on the left.

### spacing
In order to allow for standard 13mm wide adapter boards connectors should be placed no closer than 16mm apeart on a board edge (measured pin 1 to pin 1). 

### orientation
Pin 1 should always be on the top side of the board, this will make reverse connections less common.

Host connectors should generally be oriented on the right or bottom side of a board and device connectors on the left or top. 

### power connection friendly pinning
Pin 1 is always GND. Pins 9 and 10 on 10 pin connectors and pins 14 and 15 on 20 pin connectors should be 3.3V and 5V respectivly.

### galvanic isolation friendly pinning
Galvanic isolation modules (such and the iCoupler series) can support many different interfaces with one generic isolator. Care should be taken to standardize the interface such that a generic isolation device can be used for several different interface (SPI and UART for example). 
| Pin | Description | typical connection
| --- | ----------- | ----- |
| 1   | GND         |       |
| 2   | host out    | tx or bidirectional data |
| 3   | host in     | rx |
| 4   | host out    | clk |
| 5   | host in     | |
| 6   | host out    | CS |
| 7   | host in     | |
| 8   | host out    | ~reset|
| 9   | 3.3V        | |
| 10  | 5V          | | 

