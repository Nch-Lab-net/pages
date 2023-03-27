# micros()

ここは`micros()` 関数のページです

# 説明

Arduinoボードが現在のプログラムを実行し始めてから、何マイクロ秒経ったかを返します。この数値は、約70分後にオーバーフロー（0に戻る）します。Arduino Portentaファミリーのボードでは、この関数はすべてのコアで1マイクロ秒の分解能を持っています。16MHzのArduinoボード（DuemilanoveやNanoなど）では、この関数の分解能は4マイクロ秒です（つまり、返される値は常に4の倍数になります）。8MHzのArduinoボード（LilyPadなど）では、この関数は8マイクロ秒の分解能を持っています。

# 構文

`time = micros()`

# パラメータ

なし

# 返り値

Arduinoボードが現在のプログラムの実行を開始してからのマイクロ秒数を返します。型は`unsigned long`

# サンプルコード

このコードは、Arduinoボードが始まってからのマイクロ秒数を返します

```cpp
unsigned long time;

void setup() {
  Serial.begin(9600);
}
void loop() {
  Serial.print("Time: ");
  time = micros();

  Serial.println(time); // プログラムが開始してからの時間を表示
  delay(1000);          // 1秒待つ
}
```

# 注意点

1ミリ秒は1,000マイクロ秒、1秒は1,000,000（100万）マイクロ秒です

# 出典

このページは[Arduino公式のページ](https://www.arduino.cc/reference/en/language/functions/time/micros/)を翻訳したものです（一部意訳を含みます）

[一覧に戻る](https://pages.nchlab.net/Arduino/ref/)  
[トップページに戻る](https://pages.nchlab.net/)
