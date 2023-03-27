# millis()

ここは`millis()` 関数のページです

# 説明

Arduinoボードが現在のプログラムを実行し始めてから、何ミリ秒経過したかを返します。この数値は約50日後にオーバーフロー(0に戻る)します

# 構文

`time = millis()`

# パラメータ

なし

# 返り値

プログラム開始から経過した時間（ミリ秒）。型は`unsigned long`

# サンプルコード

このサンプルコードでは、Arduinoボードがコードの実行を開始してからの経過ミリ秒数をシリアルポートに表示します。

```cpp
unsigned long myTime;

void setup() {
  Serial.begin(9600);
}
void loop() {
  Serial.print("Time: ");
  myTime = millis();

  Serial.println(myTime); // プログラムが始まってからの時間を表示する
  delay(1000);            // 1秒待つ
}
```

# 注意点

`millis()`の戻り値は`unsigned long`型であり、`int` 型のような小さいデータ型で演算を行おうとすると、ロジックエラーが発生する可能性があることに注意してください。また、`符号付き long`は最大値が`unsigned long`の半分であるため、`符号付き long`でもエラーが発生する可能性があります

マイクロコントローラのタイマーを再設定すると、`millis()`の読み取りが不正確になることがあります。Arduino AVR Boards" と "Arduino megaAVR Boards" コアは、`millis()`の生成にTimer0を使用します。Arduino ARM (32-bits) Boards" と "Arduino SAMD (32-bits ARM Cortex-M0+) Boards" コアはSysTickタイマーを使用します。

# 出典

このページは[Arduino公式のページ](https://www.arduino.cc/reference/en/language/functions/time/millis/)を翻訳したものです（一部意訳を含みます）

[一覧に戻る](https://pages.nchlab.net/Arduino/ref/)  
[トップページに戻る](https://pages.nchlab.net/)
