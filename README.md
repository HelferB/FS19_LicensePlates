# Farming Simulator 19 Mod - License Plates

This mod adds support for configurable license plates in Farming Simulator 19.
Vehicles can now be registered with custom license plates.
Currently vehicles from the base game and DLCs (including the recent Grimme Pack) are supported,
but not all vehicles, since some do not have a good position for a license plate.

Additionally some vehicles from the modhub are supported,
but if you are a modder,
please follow the instructions below on how to add license plates to your vehicle.
Note: it is not necessary to add any scripts,
a simple configuration of the vehicle xml file is sufficient!

A german version is at the bottom of the file.

Eine deutsche Version ist weiter unten.

Es ist nicht notwendig mit Skripten zu arbeiten,
es genügt eine Erweiterung in der XML für das Fahrzeug!

The license plate settings of a vehicle mod overwrite the default settings of this mod.

## EN - How to add license plate support to a mod vehicle

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

*defaultSymbolColor* is the default color for the symbols on the license plates and optional.
If not preset the symbol color is black.
Possible values are black, green and red.

Since Version 1.1.0.0: *defaultBackgroundColor* is the default color for the background of the license plates and optional.
If not preset the background color is white.
Possible values are white and yellow.

Since Version 1.1.0.0: *defaultCountryCode* is the default country code.
If not present D (Germany) is used.
Possible values are AL, A, BY, B, BIH, BG, HR, CY, CZ, DK, EST, FIN, F, D, GR, H, IS, IRL, I, LV, LT, L, M, MD, MNE, NL, NMK, N, PL, P, RO, SRB, SK, SLO, E, S, CH, UA and GB.

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
This is a good option to add a default plate when this mod is not loaded.

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

## DE - Nummernschilder zu eigenen Fahrzeugen hinzufügen

Öffne das Fahrzeug mit dem Giants Editor und finde eine Position für das Nummernschild.
Mit der Tastenkombination `STRG + B` kann ein Objekt direkt an einem anderen platziert werden.
Nun öffne die XML für dein Fahrzeug und füge den folgenden Eintag im `<vehicle>` Tag hinzu:

```
	<licensePlates defaultText="1A MOD" defaultSymbolColor="green">
		<licensePlate translation="0 3.14 4.2" rotation="10 180 0" isSmall="true" hiddenNode="somePlaceholderDecal" linkNode="nodename"/>
	</licensePlates>

```
Eine kurze Erklärung für die Attribute:

*defaultText* ist ein optionaler Standardtext.
Wenn nicht angegeben ist der Text zunächst leer.
Wenn angegeben ist das Nummernschild von Beginn sichtbar.

*defaultSymbolColor* ist die optionale Standardfarbe für die Zeichen.
Wenn nicht angegeben ist die Farbe black (schwarz).
Mögliche Werte sind black, green und red.

Neu ab Version 1.1.0.0: *defaultBackgroundColor* ist die optionale Standardfarbe für den Hintergrund.
Wenn nicht angegeben ist die Farbe white (weiß).
Mögliche Werte sind white und yellow.

Neu ab Version 1.1.0.0: *defaultCountryCode* ist das standardmäßig ausgewählte Landeszeichen.
Wenn nicht angegeben wird D (Deutschland) genutzt.
If not present Germany is used.
Mögliche Werte sind AL, A, BY, B, BIH, BG, HR, CY, CZ, DK, EST, FIN, F, D, GR, H, IS, IRL, I, LV, LT, L, M, MD, MNE, NL, NMK, N, PL, P, RO, SRB, SK, SLO, E, S, CH, UA und GB.

Für jedes einzelne Nummernschild gibt es die folgenden Attribute:

*translation* ist die optionale Verschiebung des Nummernschilds.
Wenn nicht angegeben wird das Schild nicht verschoben,
was insbesondere bei Angabe einer linkNode nützlich ist.

*rotation* ist die optionale Rotation des Nummernschilds.
Wenn nicht angegeben wird das Schild nicht rotiert,
was insbesondere bei Angabe einer linkNode nützlich ist.


*isSmall* ist ein Boolean und gibt an,
dass das kleine Nummernschild genutzt werden soll.
Wenn nicht angegeben wird das normale Nummernschild genutzt.

*hiddenNode* ist eine Node,
die versteckt werden soll,
wenn das Nummernschild sichtbar ist.
Dies ist eine gute Möglichkeit um ein Platzhalterkennzeichen zu nutzen,
wenn diese Mod nicht geladen ist.

*linkNode* ist die Node,
an dem das Nummernschild angefügt wird.
Dies ist wichtig wenn sich das Nummernschild mitbewegen muss,
sei es an der Ladeluke eines Anhängers,
am Heck eines Fahrzeugs mit Knicklenkung wie Radlader,
oder an einer gefederten Fahrzeugkabine.
Verschiebung und Rotation sind relativ zu dieser Node.
Wenn nicht angegeben wird die rootNode des Fahrzeugs genutzt.
Der Wert kann auch ein String aus dem i3d Mapping sein.
*Dies ist der einfachste Weg für Modfahrzeuge.*

Mit eigenen LinkNodes in XML und I3D lässt sich das folgende Format nutzen:

```
	<licensePlates>
		<licensePlate linkNode="myLicensePlateLinkFront"/>
		<licensePlate linkNode="myLicensePlateLinkBack"/>
	</licensePlates>

```

Eine andere einfache Art ist die Übernahme einer existierenden Konfiguration von einem anderen Fahrzeug.
Dies ist praktisch bei Modfahrzeugen,
an denen nur kleine Änderungen vorgenommen wurden.
Standardtext und Standardfarbe werden aber nicht übernommen.
Es kann sich nur auf eine Konfiguration bezogen werden.
Ein Fahrzeug mit dem folgenden Eintrag übernimmt die Nummernschilder vom Fendt 500:

```
	<licensePlates>
		<parent filename="data/vehicles/fendt/favorit500/favorit500.xml"/>
	</licensePlates>

```
