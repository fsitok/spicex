# SpiceX
Netlist extraction into SPICE format for KLayout.

Note: This code used KLayout on the `dvb` branch. It's probably not stable.

## Example

```python
import pya
import spicex

"""

Netlist extraction is skipped here.
See KLayout documentation on how to extract a netlist.

"""

# Perform netlist extraction
l2n.extract_netlist()

netlist = l2n.netlist()
netlist.make_top_level_pins()
netlist.purge()
netlist.purge_nets()

# Convert KLayout netlist to a PySpice netlist.

device_class_name_to_model_mapping = {
    'NMOS': 'NMOS_VTL',
    'PMOS': 'PMOS_VTL'
}

spice_netlist = spicex.netlist_to_spice(netlist, device_class_name_to_model_mapping)

# Dump SPICE to stdout.
print(spice_netlist)

```