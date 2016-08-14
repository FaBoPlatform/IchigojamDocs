# #210 GPIO I2C Brick

<center>![](/img/200_i2c/product/210.jpg)
<!--COLORME-->

## Overview
汎用I/O拡張チップを使用したBrickです。

I2Cで8個のLEDを制御できます。

## Connecting
I2Cコネクタへ接続します。

## PCAL6408 Datasheet
| Document |
| -- |
| [PCAL6408 Datasheet](http://www.nxp.com/documents/data_sheet/PCAL6408A.pdf) |

## Register
| Slave Address |
| -- |
| 0x20 |

## Schematic
![](/img/200_i2c/schematic/210_gpio.png)

## Sample Code

I2CコネクタにGPIO Brickを接続し、GPIO Brickについている8つのLEDを左上から右下に向かって順番に点灯させます。

```
10 'FaBo Brick Sample
20 '#210 GPIO I2C Brick
30 CLS
100 'slave address
110 D=#20
200 'address set
210 POKE #800,#03,0,#01
220 POKE #810,#0,#1,#2,#4,#8,#10,#20,#40,#80
300 'init
310 A=I2CW(D,#800,1,#801,1)
320 I=0
400 'write
410 A=I2CW(D,#802,1,#810+I,1)
420 LOCATE 0,3
430 IF I>7 I=0:GOTO 510
440 I=I+1
500 'loop
510 WAIT 20
520 GOTO 410
```

## 構成Parts
- NXP PCAL6408

## GitHub
- https://github.com/FaBoPlatform/FaBo/tree/master/210_gpio
