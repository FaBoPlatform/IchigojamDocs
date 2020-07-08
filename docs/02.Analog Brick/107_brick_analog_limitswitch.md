# #107 LimitSwitch Brick

![](../img/100_analog/product/107.jpg)
<!--COLORME-->

## Overview
リミットスイッチを使ったBrickです。

I/OピンよりスイッチのON/OFFの状態を取得することができます。

機械の自動停止や位置検出の際に使用します。

## Connecting

OUTコネクタのいずれかに接続します。

## 回路図
![](../img/100_analog/schematic/107_limitswitch.png)

## Sample Code

IN1コネクタにLimitSwitch Brickを接続し、LEDコネクタに接続したLED Brickの点灯/消灯を制御しています。

```
100 ' IN(n) sample program
110 B=IN(1)
120 IF B=1 LED 1 ELSE LED 0
130 GOTO 110
```

## 構成Parts
- リミットスイッチ

## GitHub
- https://github.com/FaBoPlatform/FaBo/tree/master/107_limitswitch
