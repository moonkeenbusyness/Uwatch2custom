# Uwatch2 Custom Build Notes

This repository keeps a small Uwatch2-specific Espruino build adaptation based on:

- https://github.com/kabbi/espruino-uwatch
- https://github.com/espruino/Espruino

The local changes focus on building an application-only Espruino DFU package for a
Uwatch2 running the SD2.0.1 / SDK11-era bootloader path.

Important references:

- https://github.com/atc1441/DaFlasherFiles
- https://github.com/fanoush/ds-d6
- https://github.com/adafruit/Adafruit_nRF52_nrfutil

Do not commit generated firmware artifacts or tool archives. Keep files such as
`*.zip`, `*.hex`, `*.elf`, `*.app_hex`, toolchains, JREs, virtualenvs, and copied
bootloader binaries out of this repository. Fetch external bootloader/update files
from their upstream projects instead of redistributing them here.
