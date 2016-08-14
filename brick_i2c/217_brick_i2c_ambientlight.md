# #217 Ambient Light I2C Brick

<center>![](/img/200_i2c/product/217.jpg)
<!--COLORME-->

## Overview
照度センサーを使ったBrickです。

I2Cで明るさを取得することができます。

## Connecting
I2Cコネクタへ接続します。

## ISL29034 Datasheet
| Document |
| -- |
| [ISL29034 Datasheet](http://www.intersil.com/content/dam/Intersil/documents/isl2/isl29034.pdf) |

## Register
| Slave Address |
| -- |
| 0x44 |

## Schematic
![](/img/200_i2c/schematic/217_ambientlight.png)


## Sample Code

I2Cコネクタに接続したAmbient Light I2C Brickより明るさを取得し、画面上に表示します。

```
10 'FaBo Brick Sample
20 '#217 Ambient Light I2C Brick
30 CLS

100 'slave address
110 D=#44

200 'address set
230 POKE #800,#00,#A0,#01,1,#02

300 'init
310 A=I2CW(D,#800,1,#801,1)
320 A=I2CR(D,#802,1,#810,1)
330 ' Range #02:1600 ,Resolution #04:12bit
340 POKE #811,(PEEK(#810)&#F0)|#02|#04
350 A=I2CW(D,#802,1,#811,1)

400 'read
430 A=I2CR(D,#804,1,#820,2)
440 L=PEEK(#821)<<8+PEEK(#820)

500 'output
501 LOCATE 0,3
' range:(1600) / 12bit count :(4095) = 0.39072...
520 ?"Lux:";L/100*39+L%100*39/100;"  "

600 'loop
610 WAIT 5
620 GOTO 430
```

## 構成Parts
- Intersil ISL29034

## GitHub
- https://github.com/FaBoPlatform/FaBo/tree/master/217_ambientlight
