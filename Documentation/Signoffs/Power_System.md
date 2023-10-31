# Power Subsystem

## Function of the Subsystem

This subsystem's purpose is to allow power supplied from a wall outlet to be used in our device.


## Constraints

| No. | Constraints                                                                         | Origin            |
| --- | ----------------------------------------------------------------------------------- | ----------------- |
| 1   | The system shall convert wall AC Voltage to DC voltage | Design Constraint |
| 2   | The system shall comply with NFPA 70, in reference to all wiring and power consumption| Design Constraint/ NFPA 70 |
| 3   | The system shall not have fluctuations in voltage of greater or less than 10 volts compared to the rated voltage                          | Design Constraints |
| 4   | The system shall be able to power multpile different devices with different rated voltages | Design Constraint |
| 5   | The system shall be able to 5 VDC | Design Constraint |
| 6   | The system shall be able to 12 VDC | Design Constraint |
| 7   | The system shall have no dangerous exposed wires and shall be grounded | OSHA 1910.304 - 305 and IEC 60950-1 Safety Standards |



<sup>1</sup> All components will be powered with DC inputs, ensuring the system is more easily buildable, and more consistent between subsystems.

<sup>2</sup> While not necessarily a contraint, it is good practice to be capable of supplying 1.2x more power than is expected to be drawn. This will account for some unexpected spikes in power draw that may otherwise cause a system failure.

| Device          | Voltage |
| ----------------- | ------------------------ |
| Pulse Inverter (Capacitor Input)     | 12 V                    |
| Water Flow Valve             | 12 V                   |
| Water Flow Sensor             | 12 V                    |
| Power Sensor            |  5 V                  |
| Gas Flow Sensor           | 5 V                   |

The above table lists the rated voltages of each device.

<sup>3</sup> Different subsystems require different voltages. This will be accomplished by having 2 separate transformers to step down to appropriate voltages.

<sup>4</sup>  A typical wall outlet will be used to power the device to avoid the issue of nonstandardized outlets needed to be present in the home of the user.





## Buildable schematic 



*Figure 1. Power Subsystem buildable schematic.*


The two transformers will be taken apart and wired together manually to allow for the use of a single outlet, rather than using two seperate outlets.

## Analysis

| DEVICE            | Power |Total Power |
| ----------------- | ------------------------ | ------------------------ | 
| Pulse Inverter    | Unknown                    |                    | 
| Water Flow Valve         | 18 W                     |                    | 
| Water Level Sensor            | 60 mW                    |                    | 
| Power Sensor            | 1.55 mW                    |                   | 
| Gas Flow Sensor            | 19 mW                   |                   |
|            |                  |                   |

Pulse Inverter
The pulse inverter will be powered by 12 VDC and will have a power draw of 
~~~math
I_{Pulse Inverter} = P/V = (XW)/(12V) = XA
~~~

Water Flow Valve
The water flow valve will be powered by 12 VDC and will have a power draw of 18 W. This means the current draw is
~~~math
I_{Water Flow Valve} = P/V = (18W)/(12V) = 1.5A
~~~

Water Level Sensor
The water level sensor will be powered by 12 VDC and will have a power draw of 60 mW. This means the current draw is
~~~math
I_{Pulse Inverter} = P/V = (60mW)/(12V) = 5mA
~~~

Power Sensor
The power sensor will be powered by 5 VDC and will have a power draw of 1.55 mW. This means the current draw is
~~~math
I_{Power Sensor} = P/V = (1.55mW)/(5V) = 310μA
~~~

Gas Flow Sensor
The gas flow sensor will be powered by 5VDC and will have a power draw of 19 mW. This means the current draw is
~~~math
I_{Gas Flow Snesor} = P/V = (19mW)/(5V) = 3.8mA
~~~

The 12 VDC will be supplied by the Alitove 5050 3528.
The 5 VDC will be supplied by the Arndt 950-00143. 
These two supplies will both pull from the same outlet. The inputs of these two supplies will be spliced together in order to be able to be connected to a single wall outlet.
### Fulfilling Constraints


   There will be 2 seperate power systems: one running on 12 V, the other running on 5 V. The wall outlet will be split to 2 distinct transformers that step down to the appropriate voltages.

     

 The below equation was used for the power calculations for all devices.
~~~math
P = VI
~~~


### Power
(How much power is being used)

As mentioned previously, for the 12 V systems, the Alitove 5050 3528 Power supply will be used. This can support up to 5 A, which sould be more than enough to reliably power the system.

Again, for the 5 V systems, the Arndt 950-00143 Power supply will be used. This is a low power device, with a max current rating of 800 mA. As this is only supplying power to sensors. This should be sufficient to reliably power them.


### Input

The input for this subsystem is the 120 VAC coming from the wall outlet.

### Output

This subsystem will have 2 distinct outputs as described earlier: 12 VDC and 5 VDC. These 2 outputs can be treated as separte circuits for 
### Relay Coil

There will be a relay coil that is connected to the input of the 12 V transformer. This relay coil will be controlled by the safety subsystem, and will act as an emergency shutoff for the pulse inverter. The relay coil will receive a constant signal that allows the pulse inverter to operate. Should the signal ever not be present, the relay coil will not allow any power into the pulse inverter.


## BOM
| DEVICE            | Quantity | Price Per Unit | Total Price |
| ----------------- | -------- | -------------- | ----------- |
| Alitov 5050 3528           | 1        | $11.99         |       |
| Arndt            | 1        | $2.65          | $2.65       |
| Relay Coil            | 1       |          | $4.49       |

## References
[1] DC 12V 5A Power Supply Adapter Converter Transformer AC 100-240V input with 5.5x2.5mm DC Output Jack for 5050 3528 LED Strip Module Light, https://www.alitove.net/power-supply-adapter?product_id=65

[2] 5VDC 800mA Unregulated Linear Wall Adapter 2.5x5.5mm Center Positive, https://www.jameco.com/z/950-00143-Jameco-ReliaPro-5VDC-800mA-Unregulated-Linear-Wall-Adapter-2-5x5-5mm-Center-Positive_2231443.html
