<h2 style="padding-top:0">Everloop</h2>

### Device Compatibility

<img class="creator-compatibility-icon" src="../../img/creator-icon.svg">
<img class="voice-compatibility-icon" src="../../img/voice-icon.svg">

## Overview

The Everloop interface supports:

- Setting the RGBW colors for each individual LED.

## References

Below is the overview of the Everloop implementation. Code examples can be found [here](/matrix-hal/examples/everloop).

These header files are required to use the Everloop.

```language-cpp
// Interfaces with Everloop
#include "matrix_hal/everloop.h"
// Holds data for Everloop
#include "matrix_hal/everloop_image.h"
// Communicates with MATRIX device
#include "matrix_hal/matrixio_bus.h"
```

<details open>
<summary style="font-size: 1.75rem; font-weight: 300;">EverloopImage</summary>
`EverloopImage` is a required **object** that contains an array of `LedValue` objects.
The `EverloopImage` constructor takes in an integer representing the amount of RGBW leds your MATRIX device has.

The MatrixIOBus function `bus.MatrixLeds` outputs the number of leds on your creator.

```language-cpp
// Holds the number of LEDs on MATRIX device
int ledCount = bus.MatrixLeds();
// Create EverloopImage object, with size of ledCount
matrix_hal::EverloopImage everloop_image(ledCount);
```

`EverloopImage` holds an array full of `LedValue` objects. The `LedValue` object contains the properties `red`, `green`, `blue`, `white`. These color properties accept an RGBW integer between 0-255.

The following code shows how to set each led in everloop_image to green.

```language-cpp
// For each led, set RGBW colors
// This sets all leds to green
for (matrix_hal::LedValue &led : everloop_image.leds) {
  led.red = 0;
  led.green = 100;
  led.blue = 0;
  led.white = 0;
}
```

</details>

<details open>
<summary style="font-size: 1.75rem; font-weight: 300;">Everloop</summary>
`Everloop` is a required **object** that contains functions to interface with the Everloop on the MATRIX device.

```language-cpp
// Create Everloop object
matrix_hal::Everloop everloop;
```

The functions below are part of `Everloop`.

<details>
<summary style="font-size: 1.5rem; font-weight: 300;">.Setup</summary>
`Setup` is a **function** that takes `MatrixIOBus` object as parameter and sets that object as the bus to use for communicating with MATRIX device.

```language-cpp
// Function declaration in header file
void Setup(MatrixIOBus *bus);
```

```language-cpp
// Set everloop to use MatrixIOBus bus
everloop.Setup(&bus);
```

</details>

<details>
<summary style="font-size: 1.5rem; font-weight: 300;">.Write</summary>
`Write` is a **function** that takes an `EverloopImage` object as a parameter and updates the Everloop on the MATRIX device.

```language-cpp
// Function declaration in header file
bool Write(EverloopImage *everloop_image;
```

```language-cpp
// Updates the Everloop on the MATRIX device
everloop.Write(&everloop_image);
```

</details>
</details>