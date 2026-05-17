# ESP32-C3 Super Mini Wiring Guide

I use an **ESP32-C3 Super Mini** on my Neato Botvac D5 and the default hardware UART pins (GPIO 6 and 7) caused a hardware conflict with the internal flash/JTAG pins, freezing the serial communication.
First I've connected pins 7 and 6 but from the ESP32 and, even if the esp was connecting to the wifi and I could see the control page, no commands were given to the robot and no status was read from the robot.
To fix this, you must route your serial connections to the native hardware UART matrix on pins 20 and 21.
Instead of pin 7 use pin 21 and instead of pin 6 use pin 20.

### ESPHome Configuration Substitution
Modify your YAML substitutions to match the new hardware pins:
```yaml
substitutions:
  uart_tx: 21
  uart_rx: 20

### Wiring Diagram
Here is how the wires map out visually to the Super Mini:

| Neato Motherboard Debug Port left to right | ESP32-C3 Super Mini Pin |
| :--- | :--- |
| Pin 1 (RX) | **GPIO 21 (TX)** |
| Pin 2 (5V) | **3.3V / VCC** |
| Pin 3 (TX) | **GPIO 20 (RX)** |
| Pin 4 (GND) | **GND** |

Here also a different method and positioning of the ESP32_C3 Super Mini.

The ESP32-C3 Super Mini is placed in the hole from the bin handle in a socket making it easy to remove the micro controller without having to dismantle the robot.
<img width="2252" height="4000" alt="Final_Look" src="https://github.com/user-attachments/assets/cb387c78-5196-44e9-9f9d-c6346190ab5b" />
To realize this I used a 2x8 sockets (in the image is a 2x6 sockets)
<img width="4000" height="2252" alt="Socket" src="https://github.com/user-attachments/assets/26eeb68e-6ab7-4ead-b722-e45d0a41bfe1" />
In the hole from the bin handle I cut two paralel rectangular holes using a drill.The plastic is soft and you can cut the holes quite easy.
<img width="4000" height="2252" alt="Socket_access_via_top" src="https://github.com/user-attachments/assets/2de21744-1744-47c6-8f94-8210056514c7" />
On the back of the robot's top I've fixed the pcb with a screw, made the wiring and then isolating it with dcut tape.
<img width="4000" height="2252" alt="Socket_Wiring_with_Pin20_21" src="https://github.com/user-attachments/assets/d32f1402-16d1-4914-a52b-3a7ad6914b98" />
<img width="2252" height="4000" alt="Socket_Isolated" src="https://github.com/user-attachments/assets/17b0eb5e-d3cc-4ba8-b784-dccd15b8d9cc" />
I broke by mistake the upper plastic part of the UART so I had to solder the wires and isolate them best possible, that was ok at the end and it fitted perfectly.
<img width="4000" height="2252" alt="Uart_Port_connectivity" src="https://github.com/user-attachments/assets/57f7464a-06db-418b-8b0b-aa30de93a6d2" />
Green goes to port 21, Red to 3.3v, Grey to port 20 and Black to GND on the ESP32-C3-Mini.







