# CVE-2020-15808
A proof of concept of CVE-2020-15808 vulnerability exploit on STM32F4 Discovery board

## Requirements
* Firmware version older than 1.25.2
* Board with VCP (ex. STM32F4 discovery)
* arm-none-eabi toolchain


## Steps to reproduce the exploit
1. Move to VulnerableFirmwareF4 and compile through
   > make

    Ignore warnings due to unused variable, they are needed to ensure the compiler does not omit the variable
2. Flash build/VulnerableFirmware.elf on the device
3. Connect the Virtual Com Port
4. Get the list of connected devices through
    > lsusb
    
    Get the hex values corresponding to STM32 Virtual Com Port. They will be Vendor Id (VID) and Product Id (PID)

5. Edit main.cpp replacing to VID and PID macro with the found values. Default are for STM32F4 Discovery
6. Compile main.cpp
    > gcc main.cpp
7. Execute a.out with root permission
    > sudo ./a.out
8. In order to view the dump use 
    > hexdump -C result.bin
