# Raspberry Pi ADC hat

A Raspberry Pi hat using the Microchip MCP3424 analogue to digital
converter. The hat also has connectors for I2C and 1-wire interfaces,
and two switched outputs, for instance to control fans, motors or
relays. A Honeywell HIH6130-021 or HIH6131-021 I2C temperature and
humidity sensor can also be fitted.


## Hardware features

### Analogue to digital converter

The MCP3424 is a 4 channel 18 bit differential input analogue to
digital converter. Sample rates are 3.75 SPS (samples per second) at
18 bit resolution, 15 SPS at 16 bit resolution, 60 SPS at 14 bit
resolution and 240 SPS at 12 bit resolution. When single-ended inputs
are used the resolution is reduced by 1 bit. A jumper block enables
the I2C address of the MCP3424 to be selected from eight possible
values. The ADC inputs are directly wired to a 9 pin D connector, 3
channels can be used for differential inputs, the fourth for
single-ended measurements only. Optional decoupling capacitors can be
added to all inputs; alternatively zero ohm resistors may be used to
convert the differential inputs to single-ended.

### I2C interface

The buffered I2C interface is made available via an RJ11 connector,
allowing additional MCP3424 devices or other I2C devices to be
connected, eg the AuroraWatchNet magnetometer sensor head
(https://github.com/stevemarple/AuroraWatchNet/tree/master/hardware/FLC100_shield/remote_v2). 

### 1-wire interface

A connector for a 1-wire interface is provided. The 3 pin Molex
connector also connects to the Raspberry Pi's 3.3V supply so that it
is not necessary to use parasitic power operation.

### Power supplies

All power is used is taken from the Raspberry Pi via the GPIO
header. The 1 wire interface, I2C buffer and HAT EEPROM are connected
to the Pi's 3.3V supply, all other power is derived from the 5V
supply. Changes in the CPU load on the Pi can result in small supply
voltage variations due to voltage sag from the Pi's power supply. When
sensors and the ADC are powered directly from the Pi's 5V supply this
can result in spurious measurements. To combat this effect a DC-DC
converter and linear regulator can be fitted to derive a stable
analogue voltage supply.

### Switched outputs

Two switched outputs are provided which can be connected to fans,
motors, relays etc. Flyback diodes can be fitted to allow safe switching
of inductive loads. 
