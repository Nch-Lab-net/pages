# digitalRead()

ここは`digitalRead()` 関数のページです

# 説明

指定されたピンから`HIGH`または`LOW`として読み取ります

# 構文

`digitalRead(pin)`

# パラメータ

`pin`：読み取りたいArduinoのピン番号

# 返り値

`HIGH`または`LOW`

# サンプルコード

```cpp
int ledPin = 13;  // 13番ピンに内蔵LEDが接続されている
int inPin = 7;    //  7番ピンにプッシュボタンが接続されている
int val = 0;      // 読み取った値を保存する変数

void setup() {
  pinMode(ledPin, OUTPUT);  // 13番ピンを出力に設定
  pinMode(inPin, INPUT);    //  7番ピンを入力に設定
}

void loop() {
  val = digitalRead(inPin);   // 入力ピンの状態を読み取る
  digitalWrite(ledPin, val);  // ボタンの状態をLEDに出力
}
```

# 注意点

ピンが何にも接続されていない場合、`digitalRead()`は`HIGH`か`LOW`をランダムに出力します  
アナログ入力ピンは、A0、A1などという形でデジタルピンとして使用できます。例外は、アナログ入力としてのみ使用できるArduino Nano、Pro Mini、およびMiniのA6およびA7ピンです。

# 出典

このページは[Arduino公式のページ](https://www.arduino.cc/reference/en/language/functions/digital-io/digitalread/)を翻訳したものです（一部意訳を含みます）

[一覧に戻る](https://pages.nchlab.net/Arduino/ref/)  
[トップページに戻る](https://pages.nchlab.net/)
