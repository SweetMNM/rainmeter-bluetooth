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
To use the plugin's functions we just need to call a function whenever we want to use it and handle the output.

Example:

*New skin*

Adding the plugin to the skin
```ini
[Variables]
@include=#@#\bluetooth\bluetoothVariables.inc

@include2=#@#\bluetooth\bluetooth.inc
```
This will create a nice blue circle. that will call the **BT_TurnOnBluetooth** function **on click** (More about the BT_TurnOnBluetooth function and other functions can be found under the function section).
```ini
[MeterBluetoothOn]
Meter=Roundline
W=100
H=100
StartAngle=(Rad(270))
RotationAngle=(Rad(360))
LineStart=0
LineLength=50
LineColor=66,107,244
Solid=1
AntiAlias=1
LeftMouseUpAction=#BT_TurnOnBluetooth#
```
Now if bluetooth is off we can click our circle to turn it on.

We need to **let our user know** what's going on.

Lets add a string that will be used to update the user.
```ini
[MeterStringStatus]
Meter=String
Text=Nothing to see here
FontColor=237,249,62
FontSize=12
AntiAlias=1
Y=10R
```
the first time we want to change the status, is when the circle is pressed.

This simple action will set the **text** **option** for the **MeterStringStatus** to **Bluetooth is turnning on**. and then update the meter.

`[!SetOption MeterStringStatus Text "Bluetooth is turnning on"][!UpdateMeter MeterStringStatus]`

Lets add it to the **LeftMouseUpAction** for our circle. it should look something like this.

`LeftMouseUpAction=#BT_TurnOnBluetooth#[!SetOption MeterStringStatus Text "Bluetooth is turnning on"][!UpdateMeter MeterStringStatus]`

Then we want to let the user know when the bluetooth is on (takes about **0.5 seconds** most of the times).

This is where **functions handlers** come in handy.

Lets define a new variable in our variables section.

`BT_AfterBluetoothTurnedOn=`

The plugin knows to run this variable after the bluetooth is turned on, same thing goes for the rest of the functions.

Lets give it this value:

`[!SetOption MeterStringStatus Text "Bluetooth was turned on"][!UpdateMeter MeterStringStatus]`

We are doing the same as last time but this time we are changing the status to:

> "bluetooth was turned on"

We want the message to display for 2 seconds and then reset the message to the default message.
To achive this result we use [!Delay](https://docs.rainmeter.net/manual/bangs/#Delay)
## Functions
Most functions need to be handled after they are done executing.
For that we can define spesific actions as Variables that will be executed when our functions are done.
Don't worry if this sounds a little confusing. A couple of examples with the functions list should fix that.

### BT_CheckBluetooth
- Will check if bluetooth is ON or OFF
- Variables to handle:
  - BT_OnBluetoothCheck_On