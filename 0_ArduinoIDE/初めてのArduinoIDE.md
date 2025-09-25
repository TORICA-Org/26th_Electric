# 初めてのArduinoIDE
電装班で初めてArduinoIDEを使ってプログラミングをするよ！って人向けのガイドです．
おすすめのブログを紹介する形で進めていきます．

## RP2040/RP2350系マイコン
この設定で，以下のようなマイコンが使えるようになります．
|Raspberry Pi Pico|Seeed XIAO RP2040|
|:--:|:--:|
|<img src="https://www.switch-science.com/cdn/shop/files/eacb998e-6884-4f33-bec7-31c1b0b382b4_81409d72-9247-4783-8d4d-2f640aa3cb5b_2400x2400.jpg?v=1725604863" width="500px">|<img src="https://files.seeedstudio.com/wiki/XIAO-RP2040/img/102010428_Preview-07.jpg" width="500px">|

### インストール～初期設定～スケッチの書き込み
ロジカラブログ様のものが非常にわかりやすいです．
- [ラズパイPico/Pico2/PicoWのArduinoIDE2のインストール方法や使い方紹介 | ロジカラブログ](https://logikara.blog/raspi-pico-arduinoide/)
- [ラズパイPICO互換ボード XIAO RP2040の使い方 | ロジカラブログ](https://logikara.blog/xiao-rp2040/)
大事なところは，初期設定のままでは使えず，ボードマネージャをインストールしなければならないというところです．ボードマネージャのURLは以下にも示しておきます．
```
https://github.com/earlephilhower/arduino-pico/releases/download/global/package_rp2040_index.json
```

この種類のマイコンは電装班で1番使うので，「実践編」で使い方を学びましょう！
- [実践編](https://telling-march-c0b.notion.site/7874e2cedf9c4ff7b75fd1fb712b05d0)

## ESP32系マイコン