# Ruby logging
>Hacking on logging with Ruby

## Main idea

Logger takes a level, and only messages at that level or higher will be printed.

Levels

```
UNKNOWN	An unknown message that should always be logged.
FATAL	An unhandleable error that results in a program crash.
ERROR	A handleable error condition.
WARN	A warning.
INFO	Generic (useful) information about system operation.
DEBUG	Low-level information for developers.
```

## Features

* log a timestamp when not a tty
* override log output with DEBUG env variable

## Usage examples

```
./somecli
some unknown stuff
some fatal stuff
some error stuff
some warning stuff
some info stuff
hello world
./somecli | cat
A, [2018-03-20T16:21:06.478282 #45833]   ANY -- somecli: some unknown stuff
F, [2018-03-20T16:21:06.478379 #45833] FATAL -- somecli: some fatal stuff
E, [2018-03-20T16:21:06.478402 #45833] ERROR -- somecli: some error stuff
W, [2018-03-20T16:21:06.478419 #45833]  WARN -- somecli: some warning stuff
I, [2018-03-20T16:21:06.478441 #45833]  INFO -- somecli: some info stuff
hello world
./somecli --log-level fatal | cat
A, [2018-03-20T16:21:22.864672 #45852]   ANY -- somecli: some unknown stuff
F, [2018-03-20T16:21:22.864821 #45852] FATAL -- somecli: some fatal stuff
hello world
DEBUG=true ./somecli --log-level fatal | cat
A, [2018-03-20T16:28:22.888421 #46098]   ANY -- somecli: some unknown stuff
F, [2018-03-20T16:28:22.888517 #46098] FATAL -- somecli: some fatal stuff
E, [2018-03-20T16:28:22.888540 #46098] ERROR -- somecli: some error stuff
W, [2018-03-20T16:28:22.888558 #46098]  WARN -- somecli: some warning stuff
I, [2018-03-20T16:28:22.888574 #46098]  INFO -- somecli: some info stuff
D, [2018-03-20T16:28:22.888614 #46098] DEBUG -- somecli: "some debug stuff"
hello world
```