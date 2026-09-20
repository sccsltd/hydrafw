HydraFW official firmware for HydraBus v1
========

Ford bench fork
---------------

This fork carries the HydraBus changes used by the MK5IPC Ford bench:

* correct Lawicel/SLCAN DLC 8 and contiguous payload-byte decoding;
* non-blocking USB/CAN transmit handling for sustained emulator traffic;
* an optional `HYDRAFW_SLCAN_ONLY=1` 125 kbit/s CAN image;
* OpenOCD `FEATURE_SRST` control on PB7 for Ford SPC5 targets. PB7 is driven
  low to assert reset and changed to a high-impedance input to release it, so
  the target's 5 V reset pull-up is never driven by a 3.3 V Hydra output.
* software DFU entry using the top-level `dfu` console command or the custom
  SLCAN command `D\r` while a CAN channel is active.

The normal combined image keeps the console, CAN and JTAG modes:

```sh
cd src
make clean
make HYDRAFW_NFC=0 HYDRAFW_SLCAN_ONLY=0
```

For the MK5IPC bench, CAN2 uses PB6 (TX) and PB5 (RX) through an external
3.3 V-compatible CAN transceiver. JTAG uses PB10 (TMS), PB9 (TDO), PB8 (TDI),
PB11 (TCK), and PB7 (active-low RESET).

HydraFW is a native C (and asm) open source firmware for HydraBus v1 board.

You can Buy HydraBus v1 Online: http://hydrabus.com/buy-online

![HydraBus v1.0 Rev1.5](HydraBus_V1_0_Rev1-5_Top_Bottom.jpg)

![HydraFW default pin assignment](HydraFW_Default_PinAssignment.jpg)

* Getting Started with HydraBus v1: https://github.com/hydrabus/hydrafw/wiki/Getting-Started-with-HydraBus
* HydraFW Wiki: https://github.com/hydrabus/hydrafw/wiki
* HydraFW usage with VT100 Terminal see wiki https://github.com/hydrabus/hydrafw/wiki/HydraFW-console-commands 
* For more details on HydraBus v1 Hardware and Firmware see also: https://github.com/hydrabus/hydrabus
* For more details on HydraNFC Shield v2 see: https://github.com/hydrabus/hydrafw_hydranfc_shield_v2
* If you want to help on this project see:
  * [Coding Styles](https://github.com/hydrabus/hydrafw/blob/master/CODING_STYLE.md), [Wiki](https://github.com/hydrabus/hydrafw/wiki) & [Wiki Task List](https://github.com/hydrabus/hydrafw/wiki/Task-List) 
  * [Developer Getting-Started with HydraBus and STM32CubeIDE Windows & Linux](https://github.com/hydrabus/hydrafw/wiki/Getting-Started-with-HydraBus-and-STM32CubeIDE)
  * [How to Build/Flash/Use HydraFW on Windows](https://github.com/hydrabus/hydrafw/wiki/how-to-build-flash-and-use-hydrafw-on-windows)
  * [How to Build/Flash/Use HydraFW on Linux](https://github.com/hydrabus/hydrafw/wiki/how-to-build-flash-and-use-hydrafw-on-linux)
