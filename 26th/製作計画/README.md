# 製作計画
## 変更点
### メイン兼エアデータセンサー部
- メイン2枚+エアデータをピトー管部に集約（基板は分けるかも）
- コクピ周りのコンポーネントを減らす目的
- 表面実装化：RP2040, ICS基板, BNO055, DPS310(?)
- テレメトリ変更
  - TWILIGHT廃止（高価な割に利得が少ない）
  - XIAO ESP32C3（またはESP32C6）でTORICA_WebServer（永田作のライブラリ）による監視
- 差圧センサも表面実装に変更（ただし高価なのでそれ単体で基板を作る）
<!---
<img src="https://github.com/user-attachments/assets/a04073a2-bf50-4d67-8184-97ad48126de8" width="500px">
--->
<img src="https://github.com/user-attachments/assets/5d2e05b0-675a-4b21-9033-57a4587434e4" width="500px">

<img width="500px" alt="image" src="https://github.com/user-attachments/assets/0298a172-b9f8-4328-8565-d1b60c9bb885" />

- BNO055は続投
  - [6軸センサ内蔵モデル](https://www.switch-science.com/products/8146)のXIAOと迷ったが、変更なし
  - BNO055はマイコンを内蔵していて姿勢を計算して出力してくれる（ただの加速度センサではない）
<!--
<img src="https://github.com/user-attachments/assets/434e141c-613b-40f4-a5b1-230658cab35c" width="500px" />
-->
<img src="https://github.com/user-attachments/assets/8d33c21a-9d61-4dc3-8ca0-5c44fc5b36aa" width="800px" />  


- ドーサルフィン（ピトー管の垂直なパイプ部分を包んでいる部品）を発泡スチロールからCFRP（カーボン素材）に変更
  - バッテリー搭載位置はこの中
  - ピトー管の垂直パイプにバッテリーを外付け
- 細くするなら電動ガン用LiPo
- 3Dプリンタで防水ケースを作る
  - 厳重な水密・衝撃試験を行う必要有（危険なら市販品）
<img width="500px" alt="image" src="https://github.com/TORICA-Org/TORICA_Electric/blob/main/26th/wikiImg/airdata.png" />



### 離陸判定
- 現状の離陸判定は超音波センサだより
- プラットフォームはフェルトのような素材で、超音波が吸収されるために誤反応が多い
- プラホ上で混乱を増やしたくない
- おそらく対フェルトでも正しく認識できる、「[VL53L0X使用 レーザー測距センサーモジュール(ToF)](https://akizukidenshi.com/catalog/g/g112590/)」を組み合わせてみよう

### 操縦桿
- 3Dプリンタで造形
- できればキックバネや押しバネを使用
- 装着位置は適宜変更可能に
- 装着位置によらず操舵力は一定に

### 実装方法
- 表面実装（SMD）に変更
- リフロー（基板を焼くこと）に関する知識を定着させる
- 簡単にできるホットプレートは後日購入


## 25代電装からの継続事項
- UART通信（簡単だから）
- SDへの冗長な記録（とても重要）
- SDへの記録形式（フォーマットが変わると面倒）
- 超高効率DCDCコンバータの使用（発熱しにくいため）
- 使用言語はC/C++（TORICA_libの継続利用）

# 製作フロー
```mermaid
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```
