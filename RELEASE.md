# Cypress USB Device Middleware Library 2.0

### What's Included?

For a complete description of the USB Device Middleware, refer to README.md and the [USB Device API Reference](https://cypresssemiconductorco.github.io/usbdev/usbfs_dev_api_reference_manual/html/index.html).
The revision history of the USB Device Middleware is also available in the [API Reference Changelog](https://cypresssemiconductorco.github.io/usbdev/usbfs_dev_api_reference_manual/html/index.html#group_usb_dev_changelog).
New in this release:

* Updated the internal processing  to support USBFS driver updates.
* Significantly reduced the abort function wait time.

### Defect Fixes

* Fixed a compilation error for devices without USB hardware.

### USB Device Specific Instructions

The user must ensure that the parameters selected in the USB Device personality
are aligned with the descriptor configuration in the USB Configurator, because
there is no connection between the USB Device personality in the Device
Configurator and USB Configurator.

Specifically, parameter "Endpoints Mask" in the USB personality must be aligned
with the endpoints selected in the USB Configurator. If DMA Automatic mode is
selected, parameter  "Endpoint Buffer Size" must be aligned with the total size
of the endpoint buffers allocated in the USB Configurator.

### Known Issues

| Problem | Workaround |
| ------- | ---------- |
| The USB Device ignores LPM requests after wake up from Deep Sleep. | Call USBFS driver Cy_USBFS_Dev_Drv_Lpm_SetResponse() after calling Cy_USBFS_Dev_Drv_Resume() to restore response to the LPM packets. |
| The USB Device modes with DMA do not work after wake up from Deep Sleep, due to incorrect restore of the ARB_CFG register. | Save ARB_CFG values before entering Deep Sleep and restore it after calling of Cy_USBFS_Dev_Drv_Resume. |

### Supported Software and Tools

This version of the USB Device Middleware was validated for compatibility with the following Software and Tools:

| Software and Tools                                            | Version |
| :---                                                          | :----:  |
| ModusToolbox Software Environment                             | 2.0     |
| - ModusToolbox Device Configurator                            | 2.0     |
| - ModusToolbox USB Device Personality in Device Configurator  | 1.1     |
| - ModusToolbox USB Device Configurator                        | 2.0     |
| PSoC6 Peripheral Driver Library (PDL)                         | 1.3.0   |
| GCC Compiler                                                  | 7.2.1   |
| IAR Compiler                                                  | 8.32    |
| ARM Compiler 6                                                | 6.11    |

### More information

The following links provide more information:

* [Cypress USB Device Middleware Library Release Notes](./RELEASE.md)
* [Cypress USB Device Middleware Library API Reference](https://cypresssemiconductorco.github.io/usbdev/usbfs_dev_api_reference_manual/html/index.html)
* [PSoC 6 Peripheral Driver Library API Reference](https://cypresssemiconductorco.github.io/psoc6pdl/pdl_api_reference_manual/html/index.html)
* [ModusToolbox Software Environment, Quick Start Guide, Documentation, and Videos](https://www.cypress.com/products/modustoolbox-software-environment)
* [PSoC 6 SDK Examples](https://github.com/cypresssemiconductorco/Code-Examples-for-the-ModusToolbox-PSoC-6-SDK)
* [ModusToolbox USB Configurator Tool Guide](https://www.cypress.com/ModusToolboxUSBConfig)
* [ModusToolbox Device Configurator Tool Guide](https://www.cypress.com/ModusToolboxDeviceConfig)
* [PSoC 6 WiFi-BT Pioneer Kit](http://www.cypress.com/CY8CKIT-062-WiFi-BT)
* [PSoC 6 Wi-Fi BT Prototyping Kit](http://www.cypress.com/cy8cproto-062-4343w)
* [PSoC 6 MCU Datasheets](http://www.cypress.com/psoc6ds)
* [PSoC 6 MCU Application Notes](http://www.cypress.com/psoc6an)
* [PSoC 6 MCU Technical Reference Manuals](http://www.cypress.com/psoc6trm)
* [Cypress Semiconductor](http://www.cypress.com)

---
© Cypress Semiconductor Corporation, 2019.
