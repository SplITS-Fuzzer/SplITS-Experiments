# Fuzzing with SplITS

Within this directory, we provide numerous binaries and config files for testing, based on the set used in [Fuzzware](https://github.com/fuzzware-fuzzer/fuzzware-experiments/tree/main/02-comparison-with-state-of-the-art), with a handful of additions.

To be able to fuzz one of the provided binaries, using the pre-made configurations:
```
# Change directory to the binary you wish to test (e.g Console)
cd Console

# Set up Fuzzware environment
workon fuzzware

# Start fuzzing
fuzzware pipeline --run-for 24:00:00
```

You can adjust the time the fuzzer runs for by adjusting 24:00:00 to your desired time, in the format HH:MM:SS

To summarise the results gathered during fuzzing, you can generate coverage and crash information using:
```
fuzzware genstats coverage

fuzzware genstats crashcontexts
```
