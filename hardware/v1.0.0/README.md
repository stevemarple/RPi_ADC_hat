# Build instructions for v1.0.0

The PCB design offers a number of options for construction, not all
parts should fitted. Indeed, to do some could be harmful to the ADC
HAT and to the Raspberry Pi. Read and understand the build options first.

## Build options


### Linear voltage regulator

Decide upon the analogue supply voltage for your application. The
analogue voltage sets the operating voltage for MCP3424 ADC, and the
signal levels for the buffered section of the I2C bus. There are four
options:

1. For 3.3V operation fit a Microchip TC1262-33VDB. Do not fit the
DC-DC converter, instead fit the DC-DC converter link wire.
2. For a clean 5V analogue supply fit a Microchip MCP1790-5002E/DB
voltage regulator and a DC-DC converter.
3. To reuse the Raspberry Pi's 5V supply (not recommended) do not fit
a voltage regulator and do not fit the DC-DC converter. Fit the link
wires for both the DC-DC converter and the voltage regulator.
4. To delegate the analogue voltage supply generation to an external
board connected via the I2C interface connector X1 do not fit the
voltage regulator or the voltage regulator link wire. Whether the
DC-DC converter should also be fitted depends on the input voltage
required for the external regulator; it can be powered from either the
Pi's 5V supply or the DC-DC converter's output, selected by the
position of the jumper on JP1.

Under no circumstances should the linear regulator and its link wire
be fitted.

Fit JP1 only if option 4 is selected.


### DC-DC converter

The standard DC-DC converter is the  Traco TME0509S. Alternatives
include the Murata NME0509SC and the Recom Power RO-0509S. All
convert 5V DC to 9V DC. Provided the recommended voltage ratings for
the capacitors are followed it is also possible to use 5V to 12V DC-DC
converters.

The reference build is to include a DC-DC converter. If one is not
required then a link wire can be fitted in its place. Under no
circumstances should a DC-DC converter be fitted and its link wire.

It is also possible to use an external supply instead of the DC-DC
converter by fitting a Molex 22-23-2041 connector in its place.

If it is found that the load on the DC-DC converter is insufficient
for correct operation it is possible to fit an optional load resistor
(R3). Do not exceed power rating for the resistor; a 1210
surface-mount resistor can be fitted which is likely to have a higher
rating than the 1206 package.

### ADC

If the onboard ADC is not required (for instance, using external
devices connected to the I2C interface) then omit U4, U6, C6, C11, C12,
C13, C14, C15, C16, C17, X2 and JP2. The reference build is to fit U4,
C6, X2 and JP2.

Decoupling capacitors for the positive inputs of channels 1 (C11), 2
(C12), 3 (C13) and 4 (C14) can be fitted if required. The suggested
value is 100p but the correct value depends on application. Decoupling
capacitors for the negative differential inputs of channels 1 (C15), 2
(C16) and 3 (C17) can also be added. The correct value should probably
match the corresponding decoupling on the positive input but will vary
by application. In the case of single-ended inputs the negative
differential input can be grounded by fitting a zero ohm resistor
instead. Channel 4 is wired as single-ended input only.


### Analogue board temperature

If channel 4 of the onboard ADC is not used then the circuit board
temperature can be monitored by fitting an LM61BIM3 or LM61CIM3
temperature sensor to U6.


### Digital humidity and temperature measurement

Relative humidity can be monitored by fitting a Honeywell HIH6130-021
or HIH6131-021 sensor to U3. (Do not confuse these versions with the
similarly-named SPI versions.) Also fit C8 and C9. The sensor also
provides a digital temperature output.


### HAT EEPROM

For compliance with the HAT specifications an EEPROM must be fitted
and programmed accordingly. The recommended part is ON Semiconductor
CAT24C32WI-GT3. Larger capacities, eg ON Semiconductor CAT24C64WI-GT3,
can be fitted instead. In addition to U7 also fit R7, R8, R9, C18 and
JP3. These parts can be omitted if desired but the board cannot be
called a HAT.


### Switched outputs

Two independent switched 5V outputs can be included to control fans,
motors or relays. For the first switched output fit Q1, R10, R12 C19
and D1 and X4. For the second switched output fit Q2, R11, R13, C20,
D2 and X5. The flyback diodes are essential when inductive loads are
switched.


### External I2C interface

The buffered I2C interface can be made available to external devices
by fitting a 6P6C registered jack to X1. The external buffered side of
the I2C interface operates at the analogue supply voltage.


### 1 wire interface

If the 1 wire interface is desired fit R6 and Molex connector X3. The
interface operates at 3.3V and does not buffer the Raspberry Pi's GPIO
pins - use with caution! RJ11 connectors are frequently used for 1
wire interfaces, do not confuse the RJ11 connector used for the
external I2C interface with the 1 wire interface on the Molex
connector.


## Order of construction

The recommended general order of construction is to solder the top
side components first. Begin with the finest pitch and lowest height
components. Integrated circuits (U3, U4, and U5) should be soldered
first, then the surface mount resistors and capacitors. Then solder
the voltage regulator (U1) and FETs (Q1, Q2). If any components are to
be soldered to the underside turn over and solder those. Then add the
DC-DC converter (U2), the jumper blocks and then the
connectors. Remember that the 40 pin connector is fitted to the
underside (solder from top-side). If any link wires are to be
installed add them last, they provide the ability to test parts of the
circuit separately.

## Bill of materials (BOM)

BOMs for several different build configurations, including the
reference design, can be found in the
directory
(hardware/v1.0.0/bill_of_materials)[hardware/v1.0.0/bill_of_materials]. include:

