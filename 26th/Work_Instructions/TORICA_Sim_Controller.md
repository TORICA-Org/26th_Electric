# 作業指示書

## TORICA Sim 制御装置 (TORICA Sim Controller)

### 要件
- 電装班員ではない人間が扱っても壊れにくい仕組みにすること。
- PC↔マイコン間はUSB type-Cで接続できるようにすること。
- マイコン↔ロードセル間はUSB type-Aで接続できるようにすること。
- 静電気の多い環境に置かれる可能性を考慮し、密閉型の筐体を3Dプリンタで造形する。

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

### 24bitA/D変換基板の設計
HX711を表面実装する。
データレートを80SPSにするためにRATEピンはHIGHにする。  
![](https://theorycircuit.com/wp-content/uploads/2016/06/hx711-pin.png)

秋月で売られているA/D変換基板を参考に、ほぼパクる。使用部品も書いてあるので秋月で部品選定。  
![](img/HX711_akizuki.png)

USB type-Aは制御基板と同様に使用する。
|ピン|+5V|D-|D+|GND|
|:--:|:--:|:--:|:--:|:--:|
|用途|VDD|SLK|DOUT|GND|
|図中CN1|1|2|3|6|

ロードセルのリード線はとても細いです。  
![](https://akizukidenshi.com/img/goods/L/117556.jpg)

配線は次のようにする。  
|基板|AVDD|GND|INNA|INPA
|:--:|:--:|:--:|:--:|:--:|
|ロードセル|EXC+(赤)|EXC-(黒)|SIG-(白)|SIG+(緑)|

基板にリード線を通す穴（*Φ*2くらい）を4つ開けて、ハンダに無理な負荷がかからないようにする（下図）。ブリッジしたら嫌なので、それなりにパッド同士は離す。  
![](https://www.atmarkele.com/system/media_files/pics/000/000/334/original/03_%E3%83%AA%E3%83%BC%E3%83%89%E7%B7%9A%E3%81%AE%E3%83%95%E3%83%AC%E3%82%AD%E3%82%B7%E3%83%96%E3%83%AB%E5%9F%BA%E6%9D%BF%E3%81%B8%E3%81%AE%E7%9B%B4%E6%8E%A5%E3%83%8F%E3%83%B3%E3%83%80%E4%BB%98%E3%81%91%E4%BE%8B.png?1513572866)

A/D変換基板は4つ製作する。