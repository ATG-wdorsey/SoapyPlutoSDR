# Soapy SDR module for Pluto SDR

> **About this fork.** This fork of
> [pothosware/SoapyPlutoSDR](https://github.com/pothosware/SoapyPlutoSDR)
> carries two small fixes for streaming from a Pluto at high sample rates,
> both offered upstream as pull requests:
>
> - **No silent sample loss at 13 to 15 Msps.** The automatic RX buffer is
>   doubled at 10.5 to 15.7 Msps (262144 to 524288 samples), so a Pluto+ on
>   gigabit Ethernet streams these rates as cleanly as 16 Msps, where the
>   stock buffer is already that size
>   ([pothosware/SoapyPlutoSDR#79](https://github.com/pothosware/SoapyPlutoSDR/pull/79)).
> - **A `bufflen` buffer size survives sample rate changes** instead of being
>   reset to the automatic size
>   ([#78](https://github.com/pothosware/SoapyPlutoSDR/pull/78)).
>
> Branch `main` is upstream 0.2.3 plus both changes; `master` mirrors upstream.
> To build it, follow the instructions below with
> `git clone https://github.com/ATG-wdorsey/SoapyPlutoSDR` as the first step.

## Installation instructions

```
git clone https://github.com/pothosware/SoapyPlutoSDR
cd SoapyPlutoSDR
mkdir build
cd build
cmake ..
make
sudo make install
```

## Dependencies

- [libiio](https://github.com/analogdevicesinc/libiio)
- [libad9361](https://github.com/analogdevicesinc/libad9361-iio)
- [SoapySDR](https://github.com/pothosware/SoapySDR)

## Documentation

* https://github.com/pothosware/SoapyPlutoSDR/wiki

Note that the Frequency Correction API is not implemented,
it's recommended that you adjust the `xo_correction` value with the observed PPM in the Pluto device `config.txt`.

## PothosSDR

Note that installation with PothosSDR is optional as "PlutoSDR SoapySDR binding (experimental)" and not selected by default.

This is due to possible problems with other libusb devices,
see [#24](https://github.com/pothosware/SoapyPlutoSDR/issues/24)
and [libiio#586](https://github.com/analogdevicesinc/libiio/issues/586)

## Licensing information

GNU LESSER GENERAL PUBLIC LICENSE Version 2.1, February 1999
