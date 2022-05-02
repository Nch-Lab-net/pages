# analogWriteResolution()

ここは`analogWriteResolution()` 関数のページです

# 説明

`analogWriteResolution()`は、Arduino DueのAnalog APIを拡張したものです  
`analogWriteResolution()`は、`analogWrite()`関数の解像度を設定します。AVRベースのボードとの後方互換性のため、デフォルトは8ビット（0〜255の値）です。  

Dueは、以下のハードウェア機能を備えています。
- AVRベースのボードと同様に8ビットPWMにデフォルトで設定されている12番ピン。これは、12ビット分解能に変更することができます
- 12ビットDAC（Digital-to-Analogコンバータ）搭載2番ピン
出力の分解能を12bitに設定することで、`analogWrite()`に0～4095の値を指定してDACの分解能の全領域を利用したり、ロールオーバーせずにPWM信号を設定したりすることができます。

Zeroは、以下のようなハードウェア機能を備えています。
- AVRベースのボードと同様に8ビットPWMにデフォルトで設定されている10番ピン。これらは12ビット分解能に変更することができます
- 10ビットDAC（Digital-to-Analogコンバータ）付き1番ピン
出力の分解能を10bitに設定することで、`analogWrite()`に0から1023までの値を指定して、DACの分解能の全領域をフルに活用することができます。

MKRファミリーのボードは、以下のハードウェア機能を備えています
- AVRベースのボードと同様に8bit PWMにデフォルトで設定されている4番ピン。これらは、8bit（デフォルト）から12bit分解能に変更することができます
- 10ビットDAC（Digital-to-Analogコンバータ）付き1番ピン
出力の分解能を12bitに設定することで、`analogWrite()`に0～4095の値を指定してDACの分解能の全領域を利用できます。DACピンに10bitを設定すると、1024値のDACの分解能の全領域を利用することができます。

# 構文

`analogWriteResolution(bits)`

# パラメータ

`bits`：`analogWrite()`関数で使用する値の分解能(ビット数)を決定します。値は1〜32の範囲で指定できます。ボードのハードウェア能力よりも高いまたは低い分解能を選択した場合、`analogWrite()` で使用される値は、高すぎる場合は切り捨てられ、低すぎる場合はゼロで埋められます。詳細については、以下のノートを参照してください。

# 返り値

なし

# サンプルコード

コードの例です

```cpp
void setup() {
  // シリアル通信を開始
  Serial.begin(9600);
  // 使用するデジタルピンを出力に設定
  pinMode(11, OUTPUT);
  pinMode(12, OUTPUT);
  pinMode(13, OUTPUT);
}

void loop() {
  // A0の値を読み取り
  // LEDが接続されたピンに出力
  int sensorVal = analogRead(A0);
  Serial.print("Analog Read) : ");
  Serial.print(sensorVal);

  // デフォルトのPWM分解能
  analogWriteResolution(8);
  analogWrite(11, map(sensorVal, 0, 1023, 0, 255));
  Serial.print(" , 8-bit PWM value : ");
  Serial.print(map(sensorVal, 0, 1023, 0, 255));

  // PWM分解能を12bitに変更
  // 12bitの分解能はDueボードでのみサポートされています
  analogWriteResolution(12);
  analogWrite(12, map(sensorVal, 0, 1023, 0, 4095));
  Serial.print(" , 12-bit PWM value : ");
  Serial.print(map(sensorVal, 0, 1023, 0, 4095));

  // PWM分解能を4bitに変更
  analogWriteResolution(4);
  analogWrite(13, map(sensorVal, 0, 1023, 0, 15));
  Serial.print(", 4-bit PWM value : ");
  Serial.println(map(sensorVal, 0, 1023, 0, 15));

  delay(5);
}
```

# 注意点

`analogWriteResolution()`の値をボードの能力より高い値に設定すると、Arduinoは余分なビットを破棄します。例えば、12ビットのDACピンで`analogWriteResolution(16)`のDueを使用すると、`analogWrite()`に渡された値の最初の12ビットのみが使用され、最後の4ビットは破棄されます。

`analogWriteResolution()`の値をボードの能力より低い値に設定すると、不足するビットはゼロで埋められ、ハードウェアが要求するサイズになります。例えば、12ビットDACピンで`analogWriteResolution(8)`のDueを使用すると、Arduinoは`analogWrite()`で使用した8ビット値に4つのゼロビットを追加して、必要な12ビットを構成します。


# 出典

このページは[Arduino公式のページ](https://www.arduino.cc/reference/en/language/functions/zero-due-mkr-family/analogwriteresolution/)を翻訳したものです（一部意訳を含みます）

[一覧に戻る](https://pages.nchlab.net/Arduino/ref/)  
[トップページに戻る](https://pages.nchlab.net/)
