# 作業指示書

## TORICA Sim 制御装置 (TORICA Sim Controller)

### 要件
- 電装班員ではない人間が扱っても壊れにくい仕組みにすること。
- PC↔マイコン間はUSB type-Cで接続できるようにすること。
- マイコン↔ロードセル間はUSB type-Aで接続できるようにすること。
- 粉塵が侵入しないように、密閉型の筐体を3Dプリンタで造形する。

### 使用部品
- 類似品でも可

|部品|個数|備考|
|:--:|:--:|:--:|
|Seeed XIAO RP2040|1|USB type-Cがあるため|
|[3.5mmステレオミニプラグ](https://akizukidenshi.com/catalog/g/g105749/)|1|プラグのみ|
|[3.5mmステレオミニジャック](https://akizukidenshi.com/catalog/g/g109060/)|1|基板取付用 モノラルである必要はない|
|USB type-A メス|4|A/D変換基板接続用|

### 制御装置の基板設計
使用するマイコンはSeeed XIAO RP2040とし、これを表面実装する。以下にピン配置を示す。  
![](https://files.seeedstudio.com/wiki/XIAO-RP2040/img/xinpin.jpg)

ピンの用途は以下のようにする。
|ピン|用途|
|:--:|:--:|
|A0, A1|ラダーの可変抵抗分圧読み取り用|
|D2|リセットスイッチ|
|D3, D5, D7, D9|SLK クロック|
|D4, D6, D8, D10|DOUT データ出力|

A/D変換基盤との接続は以下のようにする。  
![](https://nettble.com/wp-content/uploads/2023/12/shot_231227_143339-1.png)

|ピン|+5V|D-|D+|GND|
|:--:|:--:|:--:|:--:|:--:|
|用途|VDD|SLK|DOUT|GND|

![](https://shop.wtihk.com/image/cache/catalog/breakoutboards/HX711/HX711_des-500x500.jpg)

3.5mmステレオミニプラグ／ジャックを用いて、ラダーを接続する。  
<img width="300px" src="https://akizukidenshi.com/img/goods/2/105749.jpg">
<img width="300px" src="https://akizukidenshi.com/img/goods/L/109060.jpg">  
それに伴って、XT↔ステレオミニプラグ変換基板も製作する。