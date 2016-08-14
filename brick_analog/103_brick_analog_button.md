# #103 Button Brick

<center>![](/img/100_analog/product/103.jpg)
<!--COLORME-->

## Overview
ボタンを使ったBrickです。I/OピンよりボタンのON/OFFの状態を取得することができます。

※ボタンカバー部分の色はランダムで送付するため色のご指定はできません。あらかじめご了承ください。

## Connecting

OUTコネクタのいずれかに接続します。

## Schematic
![](/img/100_analog/schematic/103_button.png)

## Sample Code


IN(n)

n=ポート番号（1~4）

例）<br>
IN(1)<br>
結果）<br>
押されているなら１、押されていないなら０、とIN1に接続しているボタンの状態を返す。
####注意
押したら、ではなく、押されているなら、です。
```
100 ' IN(n) sample program
110 B=IN(1)
120 IF B=1 LED 1 ELSE LED 0
130 GOTO 110
```
ボタンが押されるとIchigoJam本体のLEDが点灯します。

110 IN1に接続しているボタンの状態を変数Bに代入する。<br>
120 変数Bの値が１なら本体LEDを点灯させ、それ以外なら本体LEDを消灯させる。<br>
130 110行に移動する。（ループ）


## 構成Parts
- 12mm角タクトスイッチ

## GitHub
- https://github.com/FaBoPlatform/FaBo/tree/master/103_button
