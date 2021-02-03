# Farming Simulator 19 Mod - License Plates

This mod adds support for configurable license plates in Farming Simulator 19.
Vehicles can now be registered with custom license plates.
Currently vehicles from the base game and DLCs (including the recent Grimme Pack) are supported,
but not all vehicles, since some do not have a good position for a license plate.

Additionally some vehicles from the modhub are supported,
but if you are a modder,
please follow the instructions below on how to add license plates to your vehicle.

The license plate settings of a vehicle mod overwrite the default settings of this mod.

## How to add license plate support to a mod vehicle

Open the vehicle with the giants editor and find out where the license plates to be positioned.
A useful shortcut is `CTRL + B` to place a node directly on another.
Now open the vehicle xml file and add the following inside the `<vehicle>` tag:

```
	<licensePlates defaultText="1A MOD" defaultSymbolColor="green">
		<licensePlate translation="0 3.14 4.2" rotation="10 180 0" isSmall="true" hiddenNode="somePlaceholderDecal" linkNode="nodename"/>
	</licensePlates>

```

A short explanation of the attributes:

*defaultText* is the default text for the license plates and optional.
If not present the text of a new license plate on this vehicle is empty.
If present the license plate is visible at begin.

*defaultSymbolColor* is the default color for the license plates and optional.
IF not preset the symbol color is black.
Possible values are black, green and red.

For a single license plate the possible attributes are:

*translation* is the translation of the plate and optional.
If not present no translation is applied,
which may be especially useful when a custom linkNode is used.

*rotation* is the rotation in degrees of the plate and optional.
If not present no rotation is applied,
which may be especially useful when a custom linkNode is used.

*isSmall* is a boolean and indicates that the smaller plate should be used.
If false or not present the normal plate is used.

*hiddenNode* is a node to hide when the license plate is visible.
It is made visible again when the license plate is made invisible.
This was only added because the tipper from the Grimme DLC needed this functionality.

*linkNode* is the node to attach the license plate physically to and optional.
If the license plate should be attached to a surface that may move,
such as the back of a trailer during tipping,
or a vehicle with articulated steering like a wheelloader,
or a modern tractor with cabin suspension,
it has to be linked to that node.
This requires the translation and rotation to be relative to that node.
If not present the rootNode of the vehicle is taken.
The value can also be a string from the i3d mapping.
*This is the easiest way for mod vehicles.*

Therefore using the link node and defining nodes in the vehicle xml and i3d allows the following format:

```
	<licensePlates>
		<licensePlate linkNode="myLicensePlateLinkFront"/>
		<licensePlate linkNode="myLicensePlateLinkBack"/>
	</licensePlates>

```

Another simple way is to extend an existing configuration from another vehicle.
This is useful if a mod just makes small changes to another vehicle.
Note that default text and symbol color are not used from the parent.
Only one parent can be defined.
A vehicle with the following definition would have the license plates at the same positions as the Fendt 500:

```
	<licensePlates>
		<parent filename="data/vehicles/fendt/favorit500/favorit500.xml"/>
	</licensePlates>

```
