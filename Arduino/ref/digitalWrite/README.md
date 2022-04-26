# digitalWrite()

ここは`digitalWrite()` 関数のページです

# 説明

`HIGH`または`LOW`をデジタルピンから出力します

ピンが`pinMode()`によって`OUTPUT`として構成されている場合、その電圧はそれぞれ対応する値に設定されます。`HIGH`：5V（3.3Vボードの場合3.3V）、`LOW`：0V（GND）

ピンが`INPUT`として構成されている場合、digitalWrite() は、入力ピンの内部プルアップを有効 (HIGH) または無効 (LOW) にします。内部プルアップ抵抗を有効にするために、`pinMode()`を`INPUT_PULLUP`に設定することをお勧めします。詳細は、[デジタルピン](http://pages.nchlab.net/Arduino/ref/digital-pins/)を参照してください。

`pinMode()`を`OUTPUT`に設定せず、LEDをピンに接続して`digitalWrite(HIGH)`実行すると、LEDが暗く点灯する場合があります。`pinMode()`を明示的に設定しないと、`digitalWrite()`によって内部のプルアップ抵抗が有効になり、大きな抵抗値を持つ電流制限抵抗のように作用します。

# 構文

`digitalWrite(pin, value)`

# パラメータ

`pin` ：Arduinoのピン番号
`value` ：`HIGH`または`LOW`

# 返り値

なし

# サンプルコード

このコードでは13番ピンをOUTPUT として使用し、HIGH とLOWを1秒ごとに切り替えます

```cpp
void setup() {
  pinMode(13, OUTPUT);  //  13番ピンをOUTPUTに設定
}

void loop() {
  digitaiWrite(13, HIGH);  //  13番ピンをHIGHに設定
  delay(1000);             //  1000ミリ秒待つ
  digitaiWrite(13,  LOW);  //  13番ピンを LOWに設定
  delay(1000);             //  1000ミリ秒待つ
}
```

# 注意点

アナログ入力ピンは、A0、A1などという形でデジタルピンとして使用できます。例外は、アナログ入力としてのみ使用できるArduino Nano、Pro Mini、およびMiniのA6およびA7ピンです。

# 出典

このページは[Arduino公式のページ](https://www.arduino.cc/reference/en/language/functions/digital-io/digitalwrite/)を翻訳したものです（一部意訳を含みます）

[一覧に戻る](http://pages.nchlab.net/Arduino/ref/)
