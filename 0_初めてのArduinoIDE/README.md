# ArduinoIDE

## 本体のインストール
https://www.arduino.cc/en/software/  
最新版をインストールする．

## ボードマネージャのインストール

### Raspberry Pi PicoやSeeed XIAO RP2040など
```
https://github.com/earlephilhower/arduino-pico/releases/download/global/package_rp2040_index.json
```


## Picoにソフトウェアを書き込めないときの対処法

### USBマスストレージデバイスとして認識させる
- 動作中のプログラムなどが原因で、書き込まれる準備ができていないかもしれません。
- "BOOTSEL"ボタンを押し続けたまま、パソコンに接続し直しましょう。
- "UF2_Board"を選択して、書き込みを試みてください。

### UF2ファイルを復旧する
- 作成したソフトウェアに問題がないのにマイコンが正しく動作しない場合は、
内部のUF2ファイルが破損しているかもしれません。
- 以下の手順で解決できる場合があります。

**手順**
1. 「rp2-pico-xxxxxxxxx.uf2」をドラッグ＆ドロップ
2. 自動的にPicoが再起動
3. 復旧完了

**「rp2-pico-xxxxxxxxx.uf2」のダウンロード**
- [Pico](https://micropython.org/download/rp2-pico/rp2-pico-latest.uf2)
- [Pico W](https://micropython.org/download/rp2-pico-w/rp2-pico-w-latest.uf2)
- [Pico 2](https://micropython.org/download/RPI_PICO2/RPI_PICO2-latest.uf2)
- [Pico 2 W](https://downloads.raspberrypi.com/micropython/mp_firmware_unofficial_latest.uf2)


## 実践課題
### UART(1)
![](https://github.com/TORICA-Org/TORICA_Electric/blob/main/25th/edu3.jpg)
### UART(2)
![](https://github.com/TORICA-Org/TORICA_Electric/blob/main/25th/edu4.jpg)