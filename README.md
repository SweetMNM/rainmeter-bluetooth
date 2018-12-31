# rainmeter-bluetooth
A [rainmeter](https://www.rainmeter.net/) plugin to implement **bluetooth** functionality.

## Getting Started
rainmeter-bluetooth is **not** a usual rainmeter plugin.
the bluetooth functionality uses some batch files to toggle, turn on/off and check the bluetooth status.
To use in your skin you need to
`@include`
2 .inc files, one with some Variables, and one with the Measures used to run the batch files and get their output.

### Installing
- Clone or download this repository and unzip it.
- Go to @TODO(insert path)
- Copy @TODO(insert path)
- Paste it in your Skin's **@Resources** folder.

### Usage
After pasting the plugin's folder in your skin's **@Resources** folder.
Open your *skin.ini* file with your favorite Text editor.

Create a
[Variables](https://docs.rainmeter.net/manual/variables/) Section if you don't already have one.

Inside the Variables section [include](https://docs.rainmeter.net/manual/skins/include-option/) the first .inc file.

`@include=#@#\bluetooth\bluetoothVariables.inc`

\#@\# refers
