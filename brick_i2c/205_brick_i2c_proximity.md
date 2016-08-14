# #205 Proximity I2C Brick

<center>![](/img/200_i2c/product/205.jpg)
<!--COLORME-->

## Overview
近接センサーを使ったBrickです。

I2Cでデータを取得できます。

## Connecting
I2Cコネクタへ接続します。

## VCNL4010 Datasheet
| Document |
|:--|
| [VCNL4010 Datasheet](https://www.adafruit.com/images/product-files/466/vcnl4010.pdf) |

## Register
| I2C Slave Address |
|:-- |
| 0x13 |

## Schematic
![](/img/200_i2c/schematic/205_proximity.png)

## Sample Code

I2Cコネクタに接続したProximity I2C Brickより、センサーから物体までの距離と明るさを取得し、画面上に出力します。

```
10 'FaBo Brick Sample
20 '#205 Proximity I2C Brick
30 CLS
100 'Slave address
110 D=#13
200 'Address set
210 POKE #800,#31,#2d,#80,#82,#83,#84,#85,#87
220 POKE #810,#00,#08,#07,20,#7f,2
300 'Init
310 A=I2CW(D,#800,1,#810,1)
320 A=I2CW(D,#801,1,#811,1)
330 A=I2CW(D,#802,1,#812,1)
340 A=I2CW(D,#803,1,#812,1)
350 A=I2CW(D,#804,1,#813,1)
360 A=I2CW(D,#805,1,#814,1)
400 'Read proximity data
410 LOCATE 0,3
420 A=I2CR(D,#802,1,#820,1)
430 if (PEEK(#820)& #20) != #20 PRINT"         ":GOTO 500
440 A=I2CW(D,#807,1,#815,1)
450 A=I2CR(D,#807,1,#821,2)
460 ?"proxi:";PEEK(#822)/2+PEEK(#821)*128;"    "
500 'Read ambient data
510 if (PEEK(#820)& #40) != #40 PRINT"        ":GOTO 600
520 A=I2CW(D,#806,1,#815,1)
530 A=I2CR(D,#806,1,#823,2)
540 ?"ambi :";PEEK(#824)/2+PEEK(#823)*128;"    "
600 'loop
610 WAIT 50
620 GOTO 410
```

## Parts
- Vishay VCNL4010

## GitHub
- https://github.com/FaBoPlatform/FaBo/tree/master/205_proximity
