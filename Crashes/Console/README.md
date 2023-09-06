# Console

The Console binary contains a buffer over-read when a user inputs an invalid date. When parsing dates, the firmware attempts to compute the day of the week the given date falls on. This relies on an array lookup where the month is used as an index. Months greater than 12 exit the array bounds, and very large month values results in accessing unmapped memory.

You can run the crashing input using: ``fuzzware emu -v -M -c config.yml crash_input``
