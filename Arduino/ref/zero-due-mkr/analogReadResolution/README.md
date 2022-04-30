# analogReadResolution()

ここは`analogReadResolution()` 関数のページです

# 説明

`analogReadResolution()`は、Zero、Due、MKRファミリー、Nano 33（BLEおよびIoT）、Portenta用にAnalog APIを拡張したものです  
`analogRead()`によって返される値のサイズ(ビット数)を設定します。AVRベースのボードとの後方互換性のために、デフォルトは10ビット（0〜1023の値を返す）になっています  
Zero、Due、MKRファミリー、Nano 33（BLEおよびIoT）ボードには12ビットのADコンバータが搭載されており、分解能を12bitに変更することでその機能をフルに利用することができます。これにより、`analogRead()`の返り値は0から4095となります  
Portenta H7は16ビットADCを搭載しており、返り値は0から65535になります

# 構文

`analogReadResolution(bits)`

# パラメータ

`bits`：`analogRead()`関数が返す値の分解能(ビット数)を指定します。1から32の間で設定できます。サポートされている12ビットや16ビットよりも高い分解能を設定することはできますが、`analogRead()`で返される値は近似値になります。詳しくは、下記の注釈を参照してください。

# 返り値

なし

# サンプルコード

このコードでは、異なる解像度を持つADCを使用する方法を示しています。

```cpp
void setup() {
  // シリアル通信を開始
  Serial.begin(9600);
}

void loop() {
  // A0の値をデフォルトの分解能(10bit)として読み取り
  // シリアルモニタに出力する
  analogReadResolution(10);
  Serial.print("ADC 10-bit (default) : ");
  Serial.print(analogRead(A0));

  // 分解能を12bitに変更しA0を読み取る
  analogReadResolution(12);
  Serial.print(", 12-bit : ");
  Serial.print(analogRead(A0));

  // 分解能を16bitに変更しA0を読み取る
  analogReadResolution(16);
  Serial.print(", 16-bit : ");
  Serial.print(analogRead(A0));

  // 分解能を8bitに変更しA0を読み取る
  analogReadResolution(8);
  Serial.print(", 8-bit : ");
  Serial.println(analogRead(A0));

  // 少し処理を停止する
  delay(100);
}
```

# 注意点

`analogReadResolution()`の値を搭載されているADコンバータの分解能より高い値に設定すると、Arduinoは指定された分解能で値を返しますが、余分なビットをゼロで埋めます

例：Dueを`analogReadResolution(16)`と共に使用すると、最初の12ビットが実際にADコンバータが読み取った値、最後の4ビットがゼロで埋められた、近似の16ビットの数値が得られます

`analogReadResolution()`の値をボードの能力より低い値に設定すると、ADCから読み込まれた余分な最下位ビットは破棄されます

# 出典

このページは[Arduino公式のページ]()を翻訳したものです（一部意訳を含みます）

[一覧に戻る](http://pages.nchlab.net/Arduino/ref/)  
[トップページに戻る](http://pages.nchlab.net/)
