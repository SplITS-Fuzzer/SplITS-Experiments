# Zephyr SocketCan

Within the network module, a command “net pkt”, is defined. The handler for this command, cmd_net_pkt, takes a string parameter to the function get_net_pkt. This string is converted to a number, and is cast to a pointer. Provided the input is a valid set of hex bytes of suitable length, the pointer will be returned without error. No attempt is made to verify the data pointed to is of the net_pkt type. This pointer is then dereferenced at 0x8008c4e.

This bug was assigned the identifier CVE-2023-0779

You can run the crashing input using: ``fuzzware emu -v -M -c config.yml crash_input``
