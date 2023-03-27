# pulseInLong()

ここは`pulseInLong()` 関数のページです

# 説明

`pulseInLong()`は、`pulseIn()`の代替で、長いパルスや割り込みの影響を受けるシナリオを処理するのに適しています

ピンのパルス（`HIGH`または`LOW`）を読み取ります。例えば、値が`HIGH`の場合、`pulseInLong()`はピンが`LOW`から`HIGH`になるのを待ち、タイミングを開始し、その後ピンが`LOW`になるのを待ち、タイミングを止めます。パルスの長さをマイクロ秒単位で返すか、タイムアウト時間内に完全なパルスを受信できなかった場合は0を返します

この機能のタイミングは経験的に決定されており、短いパルスでは誤差が生じると思われます。10マイクロ秒から3分の長さのパルスで動作します。このルーチンは、割り込みが有効な場合のみ使用できます。さらに、最も高い分解能は大きなインターバルで得られます

# 構文

`pulseInLong(pin, value)`  
`pulseInLong(pin, value, timeout)`

# パラメータ

`pin`：パルスを読み取りたいArduinoのピンの番号。型は`int`  
`value`：読み取るパルスの種類（`HIGH`または`LOW`）。型は`int`  
`timeout`（オプション）：パルスが開始されるまでの秒数（マイクロ秒）。型は`unsigned int`  

# 返り値

パルスの長さ（マイクロ秒単位），またはタイムアウト前にパルスが開始されなかった場合は0。型は`unsigned long`  

# サンプルコード

この例では、7番ピンのパルスの継続時間を送信します

```cpp
int pin = 7;
unsigned long duration;

void setup() {
  Serial.begin(9600);
  pinMode(pin, INPUT);
}

void loop() {
  duration = pulseInLong(pin, HIGH);
  Serial.println(duration);
}
```

# 注意点

この関数は、`micros()`に依存しているので、`noInterrupts()`が使用されているコード内では使用できません

# 出典

このページは[Arduino公式のページ](https://www.arduino.cc/reference/en/language/functions/advanced-io/pulseinlong/)を翻訳したものです（一部意訳を含みます）

[一覧に戻る](https://pages.nchlab.net/Arduino/ref/)  
[トップページに戻る](https://pages.nchlab.net/)
