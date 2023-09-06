# Contiki NG Shell

The Contiki NG Shell fails to handle the case where a run command has fewer arguments than expected. This is the case in the cmd_rpl_set_root function. This results in a null pointer being given to the call to strcmp at 0x20761c.

You can run the crashing input using: ``fuzzware emu -v -M -c config.yml crash_input``
