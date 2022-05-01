# pulseIn()

ここは`pulseIn()` 関数のページです

# 説明

ピンのパルス（`HIGH`または`LOW`）を読み取ります。例えば、値が`HIGH`の場合、`pulseIn()`はピンが`LOW`から`HIGH`になるのを待ち、タイミングを開始し、その後ピンが`LOW`になるのを待ち、タイミングを止めます。パルスの長さをマイクロ秒で返すか、タイムアウト内に完全なパルスが受信されなかった場合は0を返します  
この機能のタイミングは経験的に決定されており、長いパルスでは誤差が生じると思われます。10マイクロ秒から3分の長さのパルスに対して動作します

備考：オプションにタイムアウトを使用すると、コードがより速く実行されます

# 構文

`pulseIn(pin, value)`  
`pulseIn(pin, value, timeout)`  

# パラメータ

`pin`：パルスを読み取りたいArduinoのピンの番号。データ型：`int`  
`value`：読み取るパルスの種類：`HIGH`か`LOW`か。データ型：`int`  
`timeout` (オプション)：パルスが始まるまで待つマイクロ秒数、デフォルトは1秒。データ型：`unsigned long`

# 返り値

パルスの長さ（マイクロ秒単位），またはタイムアウト前にパルスが開始されなかった場合は0。データ型：`unsigned long`

# サンプルコード

この例では、7番ピンのパルスの持続時間を出力しています。

```cpp
int pin = 7;
unsigned long duration;

void setup() {
  Serial.begin(9600);
  pinMode(pin, INPUT);
}

void loop() {
  duration = pulseIn(pin, HIGH);
  Serial.println(duration);
}
```

# 出典

このページは[Arduino公式のページ](https://www.arduino.cc/reference/en/language/functions/advanced-io/pulsein/)を翻訳したものです（一部意訳を含みます）

[一覧に戻る](http://pages.nchlab.net/Arduino/ref/)  
[トップページに戻る](http://pages.nchlab.net/)
