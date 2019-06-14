Atari ST keyboard USB converter
===============================

Hardware
--------
Target MCU is ATMega32u4 but other USB capable AVR will also work.
I used an RJ11 male connector to interface the keyboard.

MCU to Atari Mega STe connection
--------------------------------
MCU (+5V) - pin 1 Atari Mega STe keyboard (+5V)
MCU (+5V) - pin 2 Atari Mega STe keyboard (+5V)
MCU (Transmit (TX) data) - pin 3 Atari Mega STe keyboard (Receive (RX) data)
MCU (Receive (RX) data)  - pin 4 Atari Mega STe keyboard (Transmit (TX) data)
MCU (GND) - pin 5 Atari Mega STe keyboard (GND)
MCU (GND) - pin 6 Atari Mega STe keyboard (GND)

Arduino Pro Micro is best suited, use HW USART pins (TX1/TX0, RX1)
https://cdn.sparkfun.com/datasheets/Dev/Arduino/Boards/ProMicro16MHzv1.pdf

source:
http://www.atari-forum.com/viewtopic.php?t=28741&start=25
http://old.pinouts.ru/Inputs/atari_mega_keyb_pinout.shtml


Firmware
--------
Build:
    $ cd atari_usb
    $ make

And load the binary to MCU with your favorite programmer.

avrdude -p atmega32u4 -P /dev/ttyACM0 -c avr109 -U flash:w:atari_usb.hex

*   *   *   *   *   *   *   *   *   *   *   *   *   *   *   *   *   *


Signaling
---------
- TXD,RXD
    Asynchronous, 7812.5baud, 1-startbit(L), 8-databit, 1-stopbit(H)
		No parity

Data from keyboard
------------------
bit 7       make/break flag(0/1)
bit 6-0     following scan code


Keymap
------

see keymap.c

https://www.kernel.org/doc/Documentation/input/atarikbd.txt
(errors in the scan code table - corrected see below)

  ,-------------------------------------------------,
 / F1 / F2 / F3 / F4 / F5 / F6 / F7 / F8 / F9 / F10/
 `------------------------------------------------'
,-------------------------------------------------------------.  ,-----------. ,---------------.
| ES|  1|  2|  3|  4|  5|  6|  7|  8|  9|  0|  -|  =|  `| BS  |  |  HE | UN  | | ( | ) | / | * |
|-------------------------------------------------------------|  |------------ |---------------|
|  TB |  Q|  W|  E|  R|  T|  Y|  U|  I|  O|  P|  [|  ]|   | DE|  | IN| ^ | HO| | 7 | 8 | 9 | - |
|------------------------------------------------------   |---|  |-----------| |---------------|
|  CTR |  A|  S|  D|  F|  G|  H|  J|  K|  L|  ;|  '|   RE |ISO|  | < | v | > | | 4 | 5 | 6 | + |
|-------------------------------------------------------------'  `-----------' |-----------|---|
|  SH |  \|  Z|  X|  C|  V|  B|  N|  M|  ,|  .|  /|  SH  |                     | 1 | 2 | 3 |   |
`--------------------------------------------------------'                     |-----------| E |
       | AL|               SP                    | CL|                         |   0   | . |   |
       `---------------------------------------------'                         `---------------'

  ,-------------------------------------------------,
 / 3B / 3C / 3D / 3E / 3F / 40 / 41 / 42 / 43 / 44 /
 `------------------------------------------------'
,-------------------------------------------------------------.  ,-----------. ,---------------.
| 01| 02| 03| 04| 05| 06| 07| 08| 09| 0A| 0B| 0C| 0D| 29| 0E  |  |  62 | 61  | | 63| 64| 65| 66|
|-------------------------------------------------------------|  |------------ |---------------|
|  0F | 10| 11| 12| 13| 14| 15| 16| 17| 18| 19| 1A| 1B|   | 53|  | 52| 48| 47| | 67| 68| 69| 4A|
|------------------------------------------------------   |---|  |-----------| |---------------|
|   1D | 1E| 1F| 20| 21| 22| 23| 24| 25| 26| 27| 28|   1C | 60|  | 4B| 50| 4D| | 6A| 6B| 6C| 4E|
|-------------------------------------------------------------'  `-----------' |-----------|---|
|  2A | 2B| 2C| 2D| 2E| 2F| 30| 31| 32| 33| 34| 35|  36  |                     | 6D| 6E| 6F|   |
`--------------------------------------------------------'                     |-----------| 72|
       | 38|               39                    | 3A|                         |   70  | 71|   |
       `---------------------------------------------'                         `---------------'


Hex	Keytop
01	Esc
02	1
03	2
04	3
05	4
06	5
07	6
08	7
09	8
0A	9
0B	0
0C	-
0D	==
0E	BS
0F	TAB
10	Q
11	W
12	E
13	R
14	T
15	Y
16	U
17	I
18	O
19	P
1A	[
1B	]
1C	RET
1D	CTRL
1E	A
1F	S
20	D
21	F
22	G
23	H
24	J
25	K
26	L
27	;
28	'
29	`
2A	(LEFT) SHIFT
2B	\
2C	Z
2D	X
2E	C
2F	V
30	B
31	N
32	M
33	,
34	.
35	/
36	(RIGHT) SHIFT
37	{ NOT USED }
38	ALT
39	SPACE BAR
3A	CAPS LOCK
3B	F1
3C	F2
3D	F3
3E	F4
3F	F5
40	F6
41	F7
42	F8
43	F9
44	F10
45	{ NOT USED }
46	{ NOT USED }
47	HOME
48	UP ARROW
49	{ NOT USED }
4A	KEYPAD -
4B	LEFT ARROW
4C	{ NOT USED }
4D	RIGHT ARROW
4E	KEYPAD +
4F	{ NOT USED }
50	DOWN ARROW
51	{ NOT USED }
52	INSERT
53	DEL
54	{ NOT USED }
5F	{ NOT USED }
60	ISO KEY
61	UNDO
62	HELP
63	KEYPAD (
64	KEYPAD )
65	KEYPAD /
66	KEYPAD *
67	KEYPAD 7
68	KEYPAD 8
69	KEYPAD 9
6A	KEYPAD 4
6B	KEYPAD 5
6C	KEYPAD 6
6D	KEYPAD 1
6E	KEYPAD 2
6F	KEYPAD 3
70	KEYPAD 0
71	KEYPAD .
72	KEYPAD ENTER

