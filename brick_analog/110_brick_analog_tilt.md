# #110 Tilt Brick

<center>![](/img/100_analog/product/110.jpg)
<!--COLORME-->

## Overview
傾斜センサーを使用したBrickです。

I/Oピンより傾斜センサーの状態をデジタル値(0〜1)取得することができます。

黒い部分の中に玉が入っていて傾くとデジタル値が変化します。

LED Brickを点灯/消灯させる際などに使用します。

## Connecting

OUTコネクタのいずれかに接続します。

## Schematic
![](/img/100_analog/schematic/110_tilt.png)

## Sample Code

IN1コネクタに接続したTilt Brickの傾きによって、LEDコネクタに接続したLED Brickの点灯/消灯を制御しています。

```
100 ' IN(n) sample program
110 B=IN(1)
120 IF B=1 LED 1 ELSE LED 0
130 GOTO 110
```

## 構成Parts
- 傾斜(振動)スイッチ

## GitHub
- https://github.com/FaBoPlatform/FaBo/tree/master/110_tilt
