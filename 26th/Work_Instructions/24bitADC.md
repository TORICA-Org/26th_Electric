# 作業指示書

## 24bitA/D変換基板


### 使用部品

|部品|個数|備考|
|:--:|:--:|:--:|
|各種抵抗|任意||
|各種コンデンサ|任意||
|[HX711](https://akizukidenshi.com/catalog/g/g112473/)|6|ICのみ購入|
|USB type-A メス|4|A/D変換基板接続用|

### 基板設計
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
