# rgnd-rdrand

A simple rngd to collect entropy from Intel's Bull Mountain hwrng using the
`rdrand` instruction and feed it to the kernel's /dev/random pool.

It also throws a bit of extra entropy into /dev/urandom, because rdrand is so
cheap so why not?

## Building

	$ make

## Usage

Run as root. It takes no arguments and doesn't fork, so it's easy to run under
upstart.

## To do

* Find out what capabilities are required and drop to non-root
* Runtime configuration?
* Performance: If there's lots of room in the entropy pool, make one bigger
  buffer with more entropy rather than repeatedly adding. That syscall is the
  slowest part of the program.
