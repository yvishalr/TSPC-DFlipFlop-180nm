# Analysis of True Single Phase Clock D flip flop

The objective of the project is to compare the power consumption, speed, and area utilization of a True Single-Phase Clock (TSPC) based flip-flop with that of a conventional CMOS Master-Slave D flip-flop. By conducting a thorough analysis and comparison of the two flip-flops, the project seeks to validate the benefits of using TSPC flip-flops over conventional CMOS D flip-flops in VLSI designs.

For the MOSFETs, the 180nm technology file from the [tsmc018 library](https://sanjayvidhyadharan.in/Downloads/tsmc_180_nm/) are being used.

## Introduction to TSPC

The main motivation behind the use of TSPC logic is its ability to implement sequential logic circuits with only one clock signal, which simplifies the design and reduces the number of required clock signals. TSPC logic also provides better noise immunity and faster clock speeds compared to other clocking schemes.Moreover, TSPC logic allows for efficient implementation of dynamic logic circuits, making it a preferred choice for high-performance processors and memory circuits.

Overall, the motivation to use TSPC logic in VLSI circuits lies in its ability to improve circuit performance, reduce power consumption, and simplify the design process.

![](/resources/TSPC.png "TSPC Gate Level Circuit Diagram")

## Methodology

Both the circuits were simulated on LTSpice and analyzed over the same time period while being driven by the same inputs and having a clock frequency of 0.5 MHz. All transistors used were from the TSMC 180 nano meter tech file and both the circuits have appropriately sized transistors at L = 180nm and W = 180nm. However, every inverter has the PMOS width at 3 times the width of NMOS.

> NOTE :
>
> - All `inverter PMOS` dimensions are `W = 540n, L = 180n`
> - All `inverter NMOS` dimensions are `W = 180n, L = 180n`
> - All other `PMOS` and `NMOS` dimensions are `W = 180n, L = 180n`

### Circuit 1 : Master-Slave D flip flop

**Schematic**

![](/resources/MS/schematic.png "Schematic")

**Transient Response**

![](/resources/MS/response.png "Transient Response")

### Circuit 2 : TSPC D flip flop

**Schematic**

![](/resources/TSPC/schematic.png "Schematic")

**Transient Response**

![](/resources/TSPC/response.png "Transient Response")

## Results

On comparing the power dissipated through the source over 8 microseconds, it is found that the average output power consumption by the TSPC D flip flop is significantly lesser than the master-slave D flip flop which dissipates `56 percent more power` under the same given conditions. The TSPC alternative also uses significantly lesser number of transistors (`11 transistors`) while the latter uses `20 transistors`.

**Average power dissipation and energy consumption for Master-Slave D flip flop**

![](/resources/MS/power.png)

**Average power dissipation and energy consumption for TSPC D flip flop**

![](/resources/TSPC/power.png)

**Rise and Fall time**

Rise time is calculated as the time difference in which the output goes from 10% to 90% of its maximum value. Inversely, fall time is calculated as the time difference in which the output goes from 90% to 10% of its maximum value.

![](/resources/rise%20time%20fall%20time.png)

### Table of comparison

| Parameter                 | 11T D Flip Flop | Master-Slave D Flip Flop | Percentage Change |
| ------------------------- | --------------- | ------------------------ | ----------------- |
| **Average Power**         | 7.3763nW        | 16.706nW                 | 55.8%             |
| **Energy (over 8us)**     | 59.011fJ        | 113.67fJ                 | 48.1%             |
| **Rise Time**             | 45.72ps         | 57.84ps                  | 20.9%             |
| **Fall Time**             | 33.58ps         | 59.71ps                  | 42.85%            |
| **Number of Transistors** | 11              | 20                       | 45%               |

## Conclusion

As expected, the TSPC clocking architecture seems more efficient due to lesser number of transistors and lesser parasitic capacitance. These factors make TSPC a favourable alternative when compared to C²MOS, Domino and NORA logic.

Future work would be to make the layout of the circuit to find out the actual reduction in area. Also we can use other architectures like C²MOS, Domino and NORA logic to compare it with.

## References

- B. Razavi, "TSPC Logic [A Circuit for All Seasons]," IEEE Solid-State Circuits Magazine, Volume. 8, Issue. 4, pp. 10-13, Fall 2016
- Jiren Yuan and C. Svensson, "New single-clock CMOS latches and flipflops with improved speed and power savings," in IEEE Journal of Solid-State Circuits, vol. 32, no. 1, pp. 62-69, Jan. 1997, doi: 10.1109/4.553179
- https://www.ijrte.org/wp-content/uploads/papers/v8i1/A1382058119.pdf
- J.M. Rabaey, A. Chandrakasan – “Digital Integrated Circuits – A Design Perspective”, Second Edition, Prentice Hall Electronics and VLSI Series
