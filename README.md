# Alistair's Docker Images

## Ubuntu-Dev

This image is designed to be used with a little bash alias that I
cooked up to drop me into an ubuntized version of my current
directory. I use this to quickly switch from a macOS environment to
Ubuntu in order to build and test software (especially some C software
that I was working on that didn't support macOS at all).

To build this image:
```
cd ubuntu-dev
./buildme.sh
```

The bash alias:
```
alias dh='docker run -it --rm -v $(pwd):/work/$(basename $(pwd)) -w /work/$(basename $(pwd)) ubuntu-dev /bin/bash'
```
