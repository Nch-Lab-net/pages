# pinMode()

ここは`pinMode()` 関数のページです

## 説明

第一引数で指定されたピンが入力または出力として動作するように構成します。機能の詳細については、[デジタルピン](./../digital-pins)のページを参照してください

Arduino 1.0.1以降では第二引数を`INPUT_PULLUP` とすることでプルアップ抵抗を有効にすることができます。そのため、`INPUT` を用いるとプルアップ抵抗が明示的に無効にされます

## 構文

`pinMode(pin, mode)`

## パラメータ

`pin` ：モードを指定するArduinoのピン番号  
`mode` ：`INPUT` , `OUTPUT` または`INPUT_PULLUP`  
機能の詳細については、[デジタルピン](./../digital-pins)のページを参照してください

## 返り値

なし

## サンプルコード

このコードでは13番ピンを`OUTPUT` として使用し、`HIGH` と`LOW`を1秒ごとに切り替えます

```cpp
void setup() {
  pinMode(13, OUTPUT);  //  13番ピンをOUTPUTに設定:
}

void loop() {
  digitaiWrite(13, HIGH);  //  13番ピンをHIGHに設定
  delay(1000);             //  1000ミリ秒待つ
  digitaiWrite(13,  LOW);  //  13番ピンを LOWに設定
  delay(1000);             //  1000ミリ秒待つ
}
```

## 注意点

アナログ入力ピンは、A0、A1などという形でデジタルピンとして使用できます。例外は、アナログ入力としてのみ使用できるArduino Nano、Pro Mini、およびMiniのA6およびA7ピンです。

## 関連記事

[デジタルピンの説明](./../digital-pins)

# 出典

このページは[Arduino公式のページ](https://www.arduino.cc/reference/en/language/functions/digital-io/pinmode/)を翻訳したものです（一部意訳を含みます）

[一覧に戻る](http://pages.nchlab.net/Arduino/ref/)  
[トップページに戻る](http://pages.nchlab.net/)
