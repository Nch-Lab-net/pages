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
  pinMode(13, OUTPUT);  //13番ピンをOUTPUTに設定:
}

void loop() {
  digitaiWrite(13, HIGH);  //13番ピンをHIGHに設定:
  delay(1000);             //1000ミリ秒待つ:
  digitaiWrite(13,  LOW);  //13番ピンを LOWに設定:
  delay(1000);             //1000ミリ秒待つ:
}
```

## 注意点

アナログ入力ピンは`A0`や`A1`といった形でデジタルピンとして使用できます

## 関連記事

[デジタルピンの説明](./../digital-pins)
