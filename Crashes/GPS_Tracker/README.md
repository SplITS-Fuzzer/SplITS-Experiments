# GPS Tracker

Note: This binary contains code sections that will always crash if a string comparison is not solved. Due to the fact AFL++ does not mutate crashing seeds, these string comparisons would not normally be detected and solved. To be able to explore the firmware far enough to reach these new bugs, AFL++ was modified to run SplITS on newly discovered unique crashes. An implementation allowing this can be enabled by recompiling AFLplusplus with SPLITS_ON_CRASH defined.

## Bug 1
The firmware assumes that a connected modem will reply to the AT+GSN command with a response beginning with "AT+GSN" followed by an IMEI serial number. If no serial number is received following the AT+GSN response, the call to strtok to tokenize the string will return null. This null pointer continues to be used in gsm_get_imei() and is passed as a parameter to strlcpy, where it is dereferenced.

You can run the crashing input using: ``fuzzware emu -v -M -c config.yml crash_input1``

## Bug 2
The firmware assumes that a connected modem will reply to the AT+CCLK? command with a response containing "+CCLK: \"", and locates this string using a call to strstr(). If the substring is not found, strstr returns null, but this null value is not checked. Instead, the returned value has an offset of 8 added (at 0x80eb6), before it is passed to strtok, where the pointer is dereferenced and the firmware crashes.

You can run the crashing input using: ``fuzzware emu -v -M -c config.yml crash_input2``
