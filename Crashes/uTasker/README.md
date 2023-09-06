# uTasker

The uTasker binaries allow running memory debugging commands from the IO menu. These commands allow viewing and modification of values in memory. The provided seed attempts to access unmapped memory using these commands.

Note: Many different locations in the program can trigger this bug. Both reads and writes and varied access sizes will change the location where the crash occurs.

You can run the crashing input using: ``fuzzware emu -v -M -c config.yml crash_input``
