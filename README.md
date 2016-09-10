# Raspberry Pi ADC hat

A Raspberry Pi hat using the Microchip MCP3424 analogue to digital
converter. The hat also has connectors for I2C and 1-wire interfaces,
and two switched outputs, for instance to control fans, motors or
relays. 

## Analogue to digital converter

The MCP3424 is a 4 channel 18 bit differential input analogue to
digital converter. Sample rates are 3.75 SPS (samples per second) at
18 bit resolution, 15 SPS at 16 bit resolution, 60 SPS at 14 bit
resolution and 240 SPS at 12 bit resolution. When single-ended
(grounded) inputs are used the resolution is reduced by 1 bit. A
jumpter block enables the I2C address of the MCP3424 to be selected
from eight possible values. The ADC inputs are wired to a 9 pin D
connector, 3 channels can be used for differential inputs, the fourth
for single-ended measurements only.

## I2C interface

The buffered I2C interface is made available via an RJ11 connector,
allowing additional MCP3424 devices or other I2C devices to be
connected, eg the AuroraWatchNet magnetometer sensor head
(https://github.com/stevemarple/AuroraWatchNet/tree/master/hardware/FLC100_shield/remote_v2). 

# 1-wire interface

A connector for a 1-wire interface is provided. The 3 pin Molex
connector also connects to the Raspberry Pi's 3.3V supply so that it
is not necessary to use parasitic power operation.

