# Multi-Processing Station

# Modifications

As the robot arm uses a vacuum sucker to move tokens, it can happen, that the robot misses a token or looses it in transit.
The original model isn't able to detect such situations.

In order to add this feature, I used a standard cylinder, a standard switch and a spring feather to construct something of detecting the presence of a vacuum.

The cylinder is simply added to the connection to the sucker via t-junction and as soon as there's under-pressure, is pulls back the cylinder, which presses the switch.
As soon as the vacuum is lost, the spring feather pushes the cylinder back up and the switch is no longer pressed.

![Customization](images/customization.jpg "Customization")

With this cheap little trick I can reliably detect if the token is still "hanging on" to the robot arm.

# Hardware

For automating this model I'm using a `Beckhoff C6920-0030` PLC.
As this device has no built-in IOs I also purchased:
- `EK1100` EtherCat Bus-Coupler
- `EL1809` 16-channel digital input
- `EL2809` 16-channel digital output

The IO modules are directly connected to the bus-coupler and the bus-coupler is connected to the PLC via direct Ethernet cable.

For the communication between PLC and bus-coupler it's using the EtherCat protocol.

## I/O Connections

Here's how I connected all inputs and outputs to the PLC

### Inputs

### Outputs

# Configuration of the PLC

## I/O Configuration

# Writing the PLC Programm

## Positions

The following values are positions in the Fischertechnik factory.

| Axis           |  vert |   hor |   rot |
|----------------|------:|------:|------:|
| Register       | R4096 | R4100 | R4104 |
| Blue Bay       |   760 |   420 |   285 |
| Red Bay        |   760 |   270 |   355 |
| Green Bay      |   760 |   240 |   438 |
| Oven Intake    |   420 |   840 |   880 |
| Hig-Bay Ingest |    40 |    20 |  1324 |
| Hig-Bay Output |   120 |   220 |  1324 |
