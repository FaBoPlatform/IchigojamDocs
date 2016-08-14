# #207 Temperature I2C Brick

<center>![](/img/200_i2c/product/207.jpg)
<!--COLORME-->

## Overview
温度センサを使用したBrickです。
I2Cでデータを取得できます。

計測できる範囲は−55度〜150度です。

## Connecting
I2Cコネクタへ接続します。

## ADT7410 Datasheet
| Document |
| -- |
| [ADT7410 Datasheet](http://www.analog.com/media/en/technical-documentation/data-sheets/ADT7410.pdf) |

## Register
| Slave Address |
| -- |
| 0x48 |

## Schematic
![](/img/200_i2c/schematic/207_temperature.png)

## Sample Code

I2CコネクタにTemperature Brick(I2C)を接続し、取得した温度を画面上に出力します。

```
10 'FaBo Brick Sample
20 '#207 Temperature I2C Brick
30 CLS
100 'slave address
110 D=#48
200 'address set
210 POKE #800,#03,0,#80,0
220 POKE #810,#00,2
300 'init
310 A=I2CW(D,#800,1,#801,1)
400 'read
410 A=I2CW(D,#802,1,#803,1)
420 A=I2CW(D,#810,1,#811,1)
430 A=I2CR(D,#810,1,#820,2)
500 'output
510 LOCATE 0,3
520 T=(PEEK(#820)*256+PEEK(#821))
530 T=T*5/64
540 ?"TEMP:";
550 IF T<0 THEN T=T*-1:?"-";
560 ?T/10;".";T%5;" "
600 'loop
610 WAIT 5
620 GOTO 410
```

## 構成Parts
- Analog Devices ADT7410

## GitHub
- https://github.com/FaBoPlatform/FaBo/tree/master/207_temperature
