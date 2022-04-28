# analogReference()

ここは`analogReference()` 関数のページです

# 説明

アナログ入力に使用される基準電圧（入力範囲の上限として使用される値）を設定します。オプションは以下の通りです

Arduino AVR Boards (Uno, Mega, Leonardo など)

- `DEFAULT`: 5ボルト(5V Arduinoボード上)または3.3ボルト(3.3V Arduinoボード上)の既定のアナログ基準です
- `INTERNAL`: 内蔵の基準で、ATmega168かATmega328Pで1.1ボルト、ATmega32U4とATmega8で2.56ボルトに等しい (Arduino Megaで利用できません)
- `INTERNAL1V1`: 内蔵の1.1Vリファレンス(Arduino Megaのみ)
- `INTERNAL2V56`: 内蔵の2.56Vリファレンス(Arduino Megaのみ)
- `EXTERNAL`: AREFピンに印加される電圧(0～5Vのみ)をリファレンスとして使用します

Arduino SAMD Boards (Zero など)

- `AR_DEFAULT`：デフォルトのアナログ基準電圧3.3V
- `AR_INTERNAL`：2.23Vの内蔵リファレンス
- `AR_INTERNAL1V0`: 1.0Vの内蔵リファレンス
- `AR_INTERNAL1V65`：1.65Vの内蔵リファレンス
- `AR_INTERNAL2V23`：2.23Vの内蔵リファレンス
- `AR_EXTERNAL`：AREF端子に印加される電圧がリファレンスとして使用されます

Arduino megaAVR Boards (Uno WiFi Rev2)

- `DEFAULT`：0.55Vの内蔵リファレンス
- `INTERNAL`：0.55Vの内蔵リファレンス

VDD: ATmega4809のVdd。Uno WiFi Rev2では5V。

- `INTERNAL0V55`：0.55Vの内蔵リファレンス
- `INTERNAL1V1`：1.1Vの内蔵リファレンス
- `INTERNAL1V5`：1.5Vの内蔵リファレンス
- `INTERNAL2V5`：2.5Vの内蔵リファレンス
- `INTERNAL4V3`：4.3Vの内蔵リファレンス
- `EXTERNAL`：AREF端子に印加される電圧（0〜5Vのみ）をリファレンスとして使用します

Arduino SAM Boards (Due)

- `AR_DEFAULT`：3.3V のデフォルトのアナログ基準。これはDueで唯一サポートされているオプションです

Arduino Mbed OS Nanoボード（Nano 33 BLE）、Arduino Mbed OS Edgeボード（Edge Control）

- `AR_VDD`: デフォルトの3.3Vリファレンス
- `AR_INTERNAL`: 内蔵の0.6Vリファレンス
- `AR_INTERNAL1V2`: 1.2V リファレンス (内部 0.6 V リファレンス、2 倍のゲイン)
- `AR_INTERNAL2V4`: 2.4V リファレンス (内部 0.6 V リファレンス、4 倍のゲイン)

# 構文

`analogReference(type)`

# パラメータ

`type`：使用するタイプのリファレンス（[説明](#説明)を参照してください）

# 返り値

なし

# 注意点

アナログリファレンスを変更した後、`analogRead()`からの最初の数回の読み取りが正確でない場合があります。

**AREFピンの外部基準電圧に0V未満または5V以上のものを決して使用しないでください。AREF ピンで外部リファレンスを使用する場合は、`analogRead()` を呼び出す前に、`analogReference()`を EXTERNAL に設定する必要があります。**
そうしないと、アクティブリファレンス電圧（内部生成）とAREF端子がショートしてしまい、Arduinoボード上のマイコンにダメージを与える可能性があります。

また、外部基準電圧を5kΩの抵抗を介して`AREFピン`に接続することで、外部基準電圧と内部基準電圧を切り替えて使用することもできます。`AREFピン`には32Kの内部抵抗があるため、抵抗によってリファレンスとして使用される電圧が変化することに注意してください。この2つは分圧器として機能するため、例えば、抵抗を通して 2.5V を印加すると、AREF ピンには 2.5 * 32 / (32 + 5) = 約2.2V が供給されます。

# 出典

このページは[Arduino公式のページ](https://www.arduino.cc/reference/en/language/functions/analog-io/analogreference/)を翻訳したものです（一部意訳を含みます）

[一覧に戻る](http://pages.nchlab.net/Arduino/ref/)  
[トップページに戻る](http://pages.nchlab.net/)
