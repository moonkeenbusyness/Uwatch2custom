# Uwatch2 Custom Build Notes

このレポジトリは、UMIDIGI Uwatch2 / nRF52832 向けに Espruino をビルドするための小さな fork です。
元になっているレポジトリは以下です。

- https://github.com/kabbi/espruino-uwatch
- https://github.com/espruino/Espruino

## 目的

`DaFlasherFiles` の `DaFitBootloader23Hacked.bin` と `FitBootloaderDFU2.0.1.zip`
を使った後の SD2.0.1 / SDK11 系 bootloader に対して、application-only の
Espruino Legacy DFU zip を作ることを目的にしています。

## この fork の主な変更

- `boards/UWATCH2.py`
  - build library を `BLUETOOTH` 中心に絞る
  - DFU settings を `--application-version 0xff --sd-req 0x88` に変更
  - `NRF_SDK11=1` を指定
  - S132 2.x 前提の flash layout に調整
- `make/family/NRF52.make`
  - SDK11 のとき `gcc_startup_nrf52.s` を使う
- `scripts/intelhex/__init__.py`
  - Python 3 環境で `array.tostring()` が使えない問題を避ける

## 重要な運用メモ

生成済み firmware やローカル toolchain はこのレポジトリに入れません。
以下のようなファイルは commit しない方針です。

- `*.zip`
- `*.hex`
- `*.elf`
- `*.app_hex`
- toolchain
- JRE
- virtualenv
- DaFlasherFiles 由来の bootloader/update binary

外部 bootloader や update zip は、このレポジトリに再配布せず、必要に応じて上流から取得します。

## 参考リンク

- https://github.com/atc1441/DaFlasherFiles
- https://github.com/fanoush/ds-d6
- https://github.com/adafruit/Adafruit_nRF52_nrfutil
