# rainmeter-bluetooth
A [rainmeter](https://www.rainmeter.net/) plugin to implement **bluetooth** functionality.

## Getting Started
rainmeter-bluetooth is **not** a usual rainmeter plugin.
the bluetooth functionality uses some batch files to toggle, turn on/off and check the bluetooth status.
To use in your skin you need to
`@include`
2 .inc files, one with some Variables, and one with the Measures used to run the batch files and get their output.

### Installing
1. Clone or download this repository and unzip it.
2. Go to @TODO(insert path)
3. Copy @TODO(insert path)
4. Paste it in your Skin's **@Resources** folder.

### Adding to a skin
After pasting the plugin's folder in your skin's **@Resources** folder.
Open your *skin.ini* file with your favorite Text editor.

Create a
[Variables](https://docs.rainmeter.net/manual/variables/) Section if you don't already have one.

Inside the Variables section [include](https://docs.rainmeter.net/manual/skins/include-option/) the first .inc file.

`@include=#@#\bluetooth\bluetoothVariables.inc`

Doing that gives us access to important Variables, that later we will be able to use as actions to do some bluetooth things.

\#@\# refers to our @Resources folder and the rest of the path is our .inc file.

Below the Variables section we need to include another .inc file.

`@include2=#@#\bluetooth\bluetooth.inc`

This file contains some Measures that the actions from the first file will trigger.

Great! Now you can use the plugin from your skin.

## Usage
To use our functions we just specify the function Variables name whenever we want to use it.

E.G.
```ini
[MeterSwitch]
Meter=Image
DynamicVariables=1
Group=Tweenable
ImageName=#@#\Images\switch.png
Greyscale=1
ImageTint=#SwitchBackgroundColorActive#
W=#SwitchW#
H=#SwitchH#
```
