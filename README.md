# PlatformIO MicroMod nRF52840 Processor Support

Per
* https://learn.sparkfun.com/tutorials/micromod-nrf52840-processor-hookup-guide/arduino-software-setup
* https://github.com/sparkfun/MicroMod_Processor_Board-nRF52840.

## Usage

1. Download and open this project in VSCode with the PlatformIO extension.
2. Use the [project task](https://docs.platformio.org/en/latest/integration/ide/vscode.html#project-tasks) "Build" once. **This is expected to fail**, but needed to download the platform and packages
3. Open the folder `<home folder>\.platformio\packages\framework-arduino-mbed@3.0.1\variants`
4. Copy the `SF_MM_nRF52840_PB` folder from this repo in that `variants` folder (so that `variants\SF_MM_nRF52840_PB` exists)
5. Build again
6. You should now get

```
RAM:   [==        ]  16.2% (used 42368 bytes from 262144 bytes)
Flash: [=         ]   7.5% (used 73980 bytes from 983040 bytes)
```

## Notes

The `platformio.ini` and `SF_MM_nRF52840_PB` folder was created in accordance with the documentation linked above, specifically:
1. Screenshot shows Arduino Mbed OS core "3.0.1" must be used, which per https://github.com/platformio/platform-nordicnrf52/releases maps to `platform = nordicnrf52@9.3.0`
2. Creation of the `SF_MM_nRF52840_PB` folder per above docs with
   1. Create a copy of the ARDUINO_NANO33BLE folder in the hardware/arduino/mbed folder.
   2. Rename the copied folder to SF_MM_nRF52840_PB.
   3. Replace the variant.cpp and pins_arduino.h files in the copied folder with the files of the same name from the nRF Hardware GitHub repository.
3. Change of target variant for PlatformIO using `build_board.variant = ..` per [docs](https://docs.platformio.org/en/latest/boards/nordicnrf52/nano33ble.html#configuration) and [builder script](https://github.com/platformio/builder-framework-arduino-core-mbed/blob/36ee4ff8adb0d80d6ff15e03b34e7b10a147b4d0/arduino-core-mbed.py#L183-L186)
