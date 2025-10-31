## <b>Ux_Host_HID_Standalone Application Description</b>

This application provides an example of Eclipse USBX stack usage.
It shows how to develop bare metal USB Host Human Interface "HID" able to enumerate and communicate with a mouse or a keyboard.

The application's main calls the MX_USBX_Host_Init() function in order to Initialize USBX and USBX_Host_Process in the while loop.

As stated earlier, the present application runs in standalone mode without FreeRTOS, for this reason, the standalone variant of USBX is enabled by adding the following flag in ux_user.h:

 - #define UX_STANDALONE


The application is designed to behave as a USB HID Host, the code provides required requests to properly enumerate
HID devices, HID Class APIs to decode HID reports received from a mouse or a keyboard and display data on UART HyperTerminal.

#### <b>Expected success behavior</b>

When a HID device is plugged to NUCLEO-U385RG-Q board, a message will be displayed on the UART HyperTerminal showing
the Vendor ID and Product ID of the attached device.
After enumeration phase, a message will indicate that the device is ready for use.
The host must be able to properly decode HID reports sent by the corresponding device and display those information on the HyperTerminal.

The received HID reports are used by host to identify:

In case of a mouse:

   - (x,y) mouse position
   - Wheel position
   - Pressed mouse buttons

In case of a keyboard:

   - Pressed key

#### <b>Error behaviors</b>

Errors are detected such as (Unsupported device, Enumeration Fail) and the corresponding message is displayed on the HyperTerminal.

#### <b>Assumptions if any</b>

User is familiar with USB 2.0 "Universal Serial BUS" Specification and HID class Specification.

#### <b>Known limitations</b>

None.

#### <b>USBX usage hints</b>


### <b>Keywords</b>

Standalone, USBX Host, USB, HID, Mouse, Keyboard, UART, USART


### <b>Hardware and Software environment</b>

  - This application runs on STM32U3xx devices
  - This application has been tested with STMicroelectronics NUCLEO-U385RG-Q boards revision MB1841-U385RG-Q-D01
    and can be easily tailored to any other supported device and development board.

  - NUCLEO-U385RG-Q Set-up
    - Plug the USB HID device into the NUCLEO-U385RG-Q board through 'USB micro A-Male to A-Female' cable to the connector:
      - CN3 : to use USB High Speed DRD IP
    - Connect ST-Link cable to the PC USB port to display data on the HyperTerminal.

    A virtual COM port will then appear in the HyperTerminal:
    - Hyperterminal configuration
      - Data Length = 8 Bits
      - One Stop Bit
      - No parity
      - BaudRate = 115200 baud
      - Flow control: None

### <b>How to use it ?</b>

In order to make the program work, you must do the following :

 - Open EWARM project
 - Rebuild all files and load your image into target memory
 - Run the application

<b>Note</b>

The user has to check the list of the COM ports in Device Manager to find out the number of the COM ports that have been assigned (by OS) to the Stlink VCP.
