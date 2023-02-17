# bm832_hci_uart
Fanstel BM832 repo to use it as BLE HCI UART
It adds BM832 board support.

# Building HCI UART binaries to use Fanstel BM832 as HCI UART module
![Build artifacts](https://github.com/RomainPelletant/bm832_hci_uart/workflows/Build_HCI_UART/badge.svg?branch=main)
![Build release](https://github.com/RomainPelletant/bm832_hci_uart/workflows/Release_HCI_UART/badge.svg?tag=lastest)

# Setup environment
If cloned directly, execute inside that repo:
    west init -l
    west update

# Compile HCI UART application for BM832
west build -b fanstel_bm832 ../zephyr/samples/bluetooth/hci_uart -p

# Flash BM832
Using SWD bus with JLink, execute :
    west flash

# Usage
Pin 0.05 UART RTS
Pin 0.06 UART TX
Pin 0.07 UART CTS
Pin 0.08 UART RX
Baudrate @921600bps
HW flow control enabled

From host side, in Zephyr, setup an UART bus with
HW flow control enabled
Baudrate @921600bps
In choosen node, add:
    zephyr,bt-uart = &usartX;
with X, the UART node used.

Pin TX shall be connected to RX
Pin RX shall be connected to TX
Pin CTS shall be connected to RTS
Pin RTS shall be connected to CTS
Don't forget GND

# HCI UART with DFU
Work in progress
