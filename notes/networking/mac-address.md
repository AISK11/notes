# MAC Address

*- unique identifier for network interface controller (NIC).*

## Theory

- MAC address format: `XN:XX:XX:XX:XX:XX`
    | Description               | Address           |
    |:--------------------------|:------------------|
    | Unicast (manufacturer)    | N = [0, 4, 8, C]  |
    | Multicast (manufacturer)  | N = [1, 5, 9, D]  |
    | Unicast (administrator)   | N = [2, 6, A, E]  |
    | Multicast (administrator) | N = [3, 7, B, F]  |
    | Broadcast                 | FF:FF:FF:FF:FF:FF |
- Find MAC address manufacturer:
    - [MAC:vendor](https://www.macvendor.net/)
    - [macchanger](https://github.com/alobbs/macchanger/tree/master/data/)
