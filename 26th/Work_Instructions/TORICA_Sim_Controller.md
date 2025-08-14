# 作業指示書

## TORICA Sim 制御装置 (TORICA Sim Controller)

### 要件
- 電装班員ではない人間が扱っても壊れにくい仕組みにすること。
- PC↔マイコン間はUSB type-Cで接続できるようにすること。
- マイコン↔ロードセル間はUSB type-Aで接続できるようにすること。
- 静電気の多い環境に置かれる可能性を考慮し、密閉型の筐体を3Dプリンタで造形する。

### 制御装置の基板設計
使用するマイコンはSeeed XIAO RP2040とする。以下にピン配置を示す。  
![](https://files.seeedstudio.com/wiki/XIAO-RP2040/img/xinpin.jpg)

ピンの用途は以下のようにする。
|ピン|用途|
|:--:|:--:|
|A0|ラダーの可変抵抗分圧検出用|
|A1|ラダーの可変抵抗分圧検出用|
|D2|リセットスイッチ|
|D3, D5, D7, D9|SLK クロック|
|D4, D6, D8, D10|DOUT データ出力|

ロードセルとの接続は以下のようにする。  
![](https://nettble.com/wp-content/uploads/2023/12/shot_231227_141234-1.png)

|USB type-A|用途|
|:--:|:--:|
|+5V|VDD|
|D-|SLK|
|D+|DOUT|
|GND|GND|

![](https://shop.wtihk.com/image/cache/catalog/breakoutboards/HX711/HX711_des-500x500.jpg)

### 24bitA/D変換基板の設計
HX711を表面実装する。
データレートを80SPSにするためにRATEピンはHIGHにする。  
![](https://theorycircuit.com/wp-content/uploads/2016/06/hx711-pin.png)

![](img/HX711_akizuki.png)

USB type-Aは制御基板と同様に使用する。

ロードセルとの接続は考え中