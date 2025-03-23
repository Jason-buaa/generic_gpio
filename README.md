| Supported Targets | ESP32 | ESP32-C2 | ESP32-C3 | ESP32-C5 | ESP32-C6 | ESP32-C61 | ESP32-H2 | ESP32-P4 | ESP32-S2 | ESP32-S3 |
| ----------------- | ----- | -------- | -------- | -------- | -------- | --------- | -------- | -------- | -------- | -------- |

# Example: GPIO

(See the README.md file in the upper level 'examples' directory for more information about examples.)

This test code shows how to configure GPIO and how to use it with interruption.

Adapted for kid to play.


## GPIO functions:

| GPIO                         | Direction | Configuration                                          |
| ---------------------------- | --------- | ------------------------------------------------------ |
| CONFIG_GPIO_OUTPUT_0         | output    |                                                        |
| CONFIG_GPIO_OUTPUT_1         | output    |                                                        |
| CONFIG_GPIO_OUTPUT_2         | output    |                                                        |
| CONFIG_GPIO_INPUT_0          | input     | pulled up, interrupt from rising edge                  |
| CONFIG_GPIO_INPUT_1          | input     | pulled up, interrupt from rising edge                  |
| CONFIG_GPIO_INPUT_2          | input     | pulled up, interrupt from rising edge                  |

## Test:
 1. Connect CONFIG_GPIO_OUTPUT_0 with a button switch connected to Ground.
 2. Connect CONFIG_GPIO_OUTPUT_1 with CONFIG_GPIO_INPUT_1
 3. Connect CONFIG_GPIO_OUTPUT_2 with CONFIG_GPIO_INPUT_2
 4. Generate pulses on CONFIG_GPIO_OUTPUT_0/1/2, that triggers interrupt on CONFIG_GPIO_INPUT_0/1/2

 **Note:** The following pin assignments are used by default, you can change them by `idf.py menuconfig` > `Example Configuration`.

|                        | CONFIG_GPIO_OUTPUT_0 | CONFIG_GPIO_OUTPUT_1 | CONFIG_GPIO_OUTPUT_2| CONFIG_GPIO_INPUT_0 | CONFIG_GPIO_INPUT_1 | CONFIG_GPIO_INPUT_2 |
| ---------------------- | -------------------- | -------------------- | ------------------- | ------------------- | ------------------- | ------------------- |
| ESP32S3                | 18                   | 19                   | 20                  | 4                   | 5                   | 6                   |

## How to use example

Before project configuration and build, be sure to set the correct chip target using `idf.py set-target <chip_name>`.

### Hardware Required

* A development board with any Espressif SoC (e.g., ESP32-DevKitC, ESP-WROVER-KIT, etc.)
* A USB cable for Power supply and programming
* Some jumper wires to connect GPIOs.
* 220 Ohm Resistor *3;
* LED *3(Yellow, Red, Green);

### Configure the project

### Build and Flash

Build the project and flash it to the board, then run the monitor tool to view the serial output:

Run `idf.py -p PORT flash monitor` to build, flash and monitor the project.

(To exit the serial monitor, type ``Ctrl-]``.)

See the [Getting Started Guide](https://docs.espressif.com/projects/esp-idf/en/latest/get-started/index.html) for full steps to configure and use ESP-IDF to build projects.

## Example Output

As you run the example, you will see the following log:

```
I (277) main_task: Calling app_main()
I (277) gpio: GPIO[18]| InputEn: 0| OutputEn: 1| OpenDrain: 0| Pullup: 0| Pulldown: 0| Intr:0
I (277) gpio: GPIO[19]| InputEn: 0| OutputEn: 1| OpenDrain: 0| Pullup: 0| Pulldown: 0| Intr:0 
I (287) gpio: GPIO[20]| InputEn: 0| OutputEn: 1| OpenDrain: 0| Pullup: 0| Pulldown: 0| Intr:0
I (297) gpio: GPIO[4]| InputEn: 1| OutputEn: 0| OpenDrain: 0| Pullup: 1| Pulldown: 0| Intr:1 
I (307) gpio: GPIO[5]| InputEn: 1| OutputEn: 0| OpenDrain: 0| Pullup: 1| Pulldown: 0| Intr:1
I (307) gpio: GPIO[6]| InputEn: 1| OutputEn: 0| OpenDrain: 0| Pullup: 1| Pulldown: 0| Intr:1 

GPIO[6] intr, val: 1
GPIO[5] intr, val: 1
...
```