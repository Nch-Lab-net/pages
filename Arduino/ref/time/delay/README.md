# delay()

ここは`delay()` 関数のページです

# 説明

パラメータで指定した時間（ミリ秒）だけ、プログラムを一時停止します　　
`1000`を指定すると1秒になります

# 構文

`delay(ms)`

# パラメータ

`ms`：停止させたい時間（ミリ秒）。型は`unsigned long`

# 返り値

なし

# サンプルコード

このコードでは、出力ピンをトグルする前に、プログラムを1秒間停止させます

```cpp
int ledPin = 13;              // 13番ピンに接続されたLED

void setup() {
  pinMode(ledPin, OUTPUT);    // 使用するピンを出力に設定
}

void loop() {
  digitalWrite(ledPin, HIGH); // LEDをオンに設定
  delay(1000);                // 1秒停止
  digitalWrite(ledPin, LOW);  // LEDをオフに設定
  delay(1000);                // 1秒停止
}
```

# 注意点

delay関数でLEDを点滅させるのは簡単で、多くのスケッチがスイッチのデバウンスなどのタスクに短い遅延を使用していますが、スケッチの中で`delay()`を使用することには大きな欠点があります。delay関数の実行中は、センサーの読み取り、数学的計算、ピンの操作などを行うことができないため、事実上、他のほとんどのアクティビティを停止させることになります  
タイミングを制御する別のアプローチとして、[Blink Without Delay](http://arduino.cc/en/Tutorial/BlinkWithoutDelay)スケッチを参照してください。このスケッチでは、十分な時間が経過するまで`millis()`関数をポーリングしながらループしています。Arduinoスケッチが非常に単純でない限り、10ミリ秒以上のイベントのタイミングに`delay()`を使用することは、より知識のあるプログラマには通常避けられるでしょう  
しかし、delay関数がAtmegaチップを制御している間、あることが進行します。delay関数は割り込みを無効にしないためです。RXピンに現れるシリアル通信は記録され、PWM（analogWrite）の値とピンの状態は維持され、割り込みはあるべきように動作します

# 出典

このページは[Arduino公式のページ](https://www.arduino.cc/reference/en/language/functions/time/delay/)を翻訳したものです（一部意訳を含みます）

[一覧に戻る](https://pages.nchlab.net/Arduino/ref/)  
[トップページに戻る](https://pages.nchlab.net/)
