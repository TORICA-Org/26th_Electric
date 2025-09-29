# 作業指示書

## 桁焼き記録装置 (Ketayaki Recorder)

### 要件
- 桁焼きの温度推移をTFT液晶で確認できるようにするとともに、SDカードに記録すること。
- 筐体は3Dプリンタで造形し、破壊しにくい構造にすること。
- 9/9までに完成させること。

### 使用部品
- 本装置1つあたりの使用部品
- 類似品でも可

|部品|個数|備考|
|:--:|:--:|:--:|
|[Raspberry Pi Pico](https://akizukidenshi.com/catalog/g/g116132/)|1||
|[MSP2807(ILI9341)](https://akizukidenshi.com/catalog/g/g116265/)|1|SDカードスロットを内蔵|
|[電池ボックス 単3×3本](https://akizukidenshi.com/catalog/g/g102667/)|1||
|単3電池|3|翼班のあまりを使用|
|[高感度高耐熱サーミスター](https://akizukidenshi.com/catalog/g/g111896/)|1|B定数：4126|
|[3.5mmモノラルミニプラグ](https://akizukidenshi.com/catalog/g/g112523/)|1|プラグのみ|
|[3.5mmステレオミニジャック](https://akizukidenshi.com/catalog/g/g109060/)|1|基板取付用 モノラルである必要はない|
|[3Pトグルスイッチ レバーロック式](https://akizukidenshi.com/catalog/g/g112710/)|1|これまでもメイン電装で使用|
|[他励式ブザー](https://akizukidenshi.com/catalog/g/g104118/)|1|圧電スピーカー(圧電サウンダー)|
|SDカード|任意|32GB以下が好ましい|
|PCB基板|1|27代が作る|
|3Dプリンタ製の筐体|1|27代が作る|

### Kikadによる回路設計
以下にソフトウェアのピン定義マクロを示す。これに従って回路図を作成すること。  
その際、ネットラベルを用いて配線すること。

```cpp
// ============ Picoのピン設定============

// SPI通信用
#define TFT_TOUCH_SD_MOSI 19 // MOSI(SDI) 送信(TX) 共通
#define TOUCH_SD_MISO 16     // MISO(SDO) 受信(RX) 共通
#define TFT_TOUCH_SD_SCK 18  // SCK クロック
#define TFT_CS 22            // TFT液晶のチップセレクト
#define TOUCH_CS 17          // タッチスクリーンのチップセレクト
#define SD_CS 27             // SDカードスロットのチップセレクト

// TFT液晶用
#define TFT_RST 21 // Reset 
#define TFT_DC 20  // D/C

#define sound 28 // 他励式ブザー用

const int Pin_thermistor = 26; // サーミスタ用

// =======================================
```

Raspberry Pi Picoのピン配置も示しておく。ピン番号はGP〇〇と書いてある。  
<img src="https://res.cloudinary.com/zenn/image/fetch/s--nzJFdVY2--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_1200/https://storage.googleapis.com/zenn-user-upload/deployed-images/8f8bb113d297d40f9cb9f24d.png%3Fsha%3D4f37de9c32dbf24ed7731598711163e7c438f3ee">

TFT液晶のピン配置も示しておく。  
<img src="https://tamanegi-digick.com/wp-content/uploads/2024/05/ili9341_pin.jpg">

- 電源は単3電池3本の4.5Vとする。
  - 電池ボックスのリード線にXHコネクタを取り付けて基板と接続する。
  - この4.5Vは **VSYS** に対して供給する。(1.8V〜5.5Vの電源を使用する事ができる)
  - 3Dプリンタで造形した筐体側にマジックテープで固定する。

- サーミスタは[モノラルミニプラグ](https://akizukidenshi.com/catalog/g/g112523/)及び[ステレオミニジャック](https://akizukidenshi.com/catalog/g/g109060/)で接続する。  
<img width="300px" src="https://akizukidenshi.com/img/goods/3/112523.jpg">
<img width="300px" src="https://akizukidenshi.com/img/goods/L/109060.jpg">

- 他励式ブザーは基板上に実装する。

- TFT液晶と基板の接続はピンヘッダによって行う。
  - Raspberry Pi PicoとTFT液晶はそれぞれ基板の両面に配置する。
  - **TFT液晶のピン配置を反転**させる必要があるため要注意。(TFT液晶の裏面にあるシルクスクリーン【下図】を参考に設計するのが良い)  
  ![](https://abacasstorageaccnt.blob.core.windows.net/cirkit/1d8ef4dc-d8a3-425d-96df-f8d4e71a26b5.jpg)
  - TFT液晶側にあるネジで固定し、基板はネジ止めしない。
  - TFT液晶のピンヘッダの間にPicoをSDカードスロット寄りに配置する。(既製品Picoは表面実装するかも)

- これまでメイン電装に使用していたロック付きのトグルスイッチを本装置のメインスイッチにする。
  - 他の部員に触らせておくことで、このスイッチに慣れさせる目的。

- 桁焼き記録装置は2つ製作する。
