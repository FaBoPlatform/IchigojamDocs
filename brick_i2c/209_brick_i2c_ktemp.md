# #209 Ktemp I2C Brick

<center>![](/img/200_i2c/product/209.jpg)
<!--COLORME-->

## Overview
K型熱電対を接続できるBrickです。
I2Cでデータを取得できます。

## Connecting
I2Cコネクタへ接続します。


## MCP3421 Datasheet
| Document |
| -- |
| [MCP3421 Datasheet](http://ww1.microchip.com/downloads/en/DeviceDoc/22003e.pdf) |

## Register
| Slave Address |
| -- |
| 0x68 - 0x6F |
MCP3421のSlave Addressは0x68〜0x6Fのものが存在し、その値は工場出荷時に決まっており、後から変更することはできません。
FaBoBrickでは、0x68、または0x69の２種類を使用しています。

## Schematic
![](/img/200_i2c/schematic/209_ktemp.png)


## Sample Code

このサンプルは、I2Cコネクタに接続したKtemp BrickにK型熱電対を接続し、熱電対から取得した値を温度に変換し画面上に出力します。

```
10 'FaBo Brick Sample
20 '#209 Ktemp I2C Brick
30 CLS
100 'slave address #68-#6F
110 D=#68

200 'address set
210 POKE #800,#9f,0,4

300 'init
310 A=I2CW(D,#800,1,#801,1)

400 'read
410 A=I2CR(D,#800,1,#810,4)
420 IF PEEK(#810) & 0xFF THEN S=1 ELSE S=0
430 T=PEEK(#811)<<8 | PEEK(#812)
440 T=T/128*125+T%128*125/128 +500:'(T*1000)/1024+500
450 T=T/3

500 'output
510 LOCATE 0,3
520 ?"KTEMP:";
530 IF T<0 THEN T=T*-1:?"-";
540 ?T/10;".";T%10;"  ":'T/10

600 'loop
610 WAIT 5
620 GOTO 410
```

## 構成Parts
- Microchip Technology MCP3421

## GitHub
- https://github.com/FaBoPlatform/FaBo/tree/master/209_ktemp
