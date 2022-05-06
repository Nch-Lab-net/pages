# shiftOut()

ここは`shiftOut()` 関数のページです

# 説明

1バイトのデータを1ビットずつシフトアウトします。最上位ビット（すなわち左端）または最下位ビット（右端）から開始します。各ビットは順番にデータピンに書き込まれ、その後、クロックピンからパルスを送信し、そのビットの値を確定させます

注意：立ち上がりエッジでクロック駆動するデバイスと接続する場合は、`shiftOut()`を呼び出す前にクロックピンがLowであることを確認する必要があります（例：`digitalWrite(clockPin, LOW)`を呼び出すなど）

これはソフトウェアによる実装です。SPIライブラリも参照してください。

# 構文

`shiftOut(dataPin, clockPin, bitOrder, value)`

# パラメータ

`dataPin`：各bitのデータを出力するピン。型は`int`  
`clockPin`：`dataPin`にデータがセットされた際にトグルされるピン。型は`int`  
`bitOrder`：`MSBFIRST`または`LSBFIRST`のどちらからビットをシフトさせるかを指定します。**MSBFIRST**は最上位ビットからの読み出し、**LSBFIRST**は最下位ビットからの読み出しを意味します  
`value`：シフトアウトさせるデータ。型は`byte`  

# 返り値

なし

# サンプルコード

付属の回路は、[74HC595シフトレジスタの制御のチュートリアル](https://www.arduino.cc/reference/en/language/functions/advanced-io/shiftout/#:~:text=tutorial%20on%20controlling%20a%2074HC595%20shift%20register)をご覧ください。

```cpp
//**************************************************************//
//  Name    : shiftOutCode, Hello World                         //
//  Author  : Carlyn Maw,Tom Igoe                               //
//  Date    : 25 Oct, 2006                                      //
//  Version : 1.0                                               //
//  Notes   : Code for using a 74HC595 Shift Register           //
//          : to count from 0 to 255                            //
//****************************************************************

// 74HC595 の ST_CP に接続されたピン
int latchPin = 8;
// 74HC595 の SH_CP に接続されたピン
int clockPin = 12;
// 74HC595の DS に接続されたピン
int dataPin = 11;

void setup() {
  //各ピンを出力に設定
  pinMode(latchPin, OUTPUT);
  pinMode(clockPin, OUTPUT);
  pinMode(dataPin, OUTPUT);
}

void loop() {
  // カウントアップルーチン
  for (int j = 0; j < 256; j++) {
    // データを送るためにlatchPinをLOWレベルにする
    digitalWrite(latchPin, LOW);
    shiftOut(dataPin, clockPin, LSBFIRST, j);
    // latchPinをHIGHに戻す
    digitalWrite(latchPin, HIGH);
    delay(1000);
  }
}
```

# 注意点

dataPinとclockPinは既に[pinMode()](./../digital-io/pinMode)の呼び出しによって出力として設定されている必要があります

shiftOutは現在1バイト（8ビット）出力するように書かれているので、255より大きな値を出力するためには2段階の操作が必要です

```cpp
// MSBFIRSTの場合の手順
int data = 500;
// 上位8bitを送信
shiftOut(dataPin, clock, MSBFIRST, (data >> 8));
// 下位8bitを送信
shiftOut(dataPin, clock, MSBFIRST, data);

// LSBFIRSTの場合の手順
data = 500;
// 下位8bitを送信
shiftOut(dataPin, clock, LSBFIRST, data);
// 上位8bitを送信
shiftOut(dataPin, clock, LSBFIRST, (data >> 8));
```

# 出典

このページは[Arduino公式のページ](https://www.arduino.cc/reference/en/language/functions/advanced-io/shiftout/)を翻訳したものです（一部意訳を含みます）

[一覧に戻る](https://pages.nchlab.net/Arduino/ref/)  
[トップページに戻る](https://pages.nchlab.net/)
