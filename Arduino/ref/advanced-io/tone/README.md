# tone()

ここは`tone()` 関数のページです

# 説明

指定された周波数の矩形波（および50%のデューティサイクル）を指定されたピンから出力します。継続時間を指定することができ、指定しない場合は`noTone()`を呼び出すまで続きます。このピンにブザーなどを接続することによって任意の周波数の音を鳴らすことができます。

一度に出力できる波形は1つだけです。すでに別のピンで音が鳴っている場合、`tone()`を呼び出しても何も起こりません。すでに`tone()`を実行して波形を出力している状態のピンに対して`tone()`を呼び出すと、新たに指定された周波数が出力されます

`tone()`関数を使用すると、（Mega以外のボードでは）3番ピンと11番ピンのPWM出力と干渉します

31Hzより低い音を発生させることはできません。技術的な詳細については、[Brett Hagmanのノート](https://github.com/bhagman/Tone#ugly-details)を参照してください。

# 構文

`tone(pin, frequency)`
`tone(pin, frequency, duration)`

# パラメータ

`pin`：波形を出力させたいピンを指定  
`frequency`：出力させたい周波数をHzで指定。型は`unsigned int`  
`duration`：出力を継続させたい時間をミリ秒で指定（オプション）。型は`unsigned int`  

# 返り値

なし

# 注意点

複数のピンで異なる音程を鳴らしたい場合は、すでに出力しているピンに対し`noTone()`を実行してから、次のピンで`tone()`を呼び出す必要があります。

# 出典

このページは[Arduino公式のページ](https://www.arduino.cc/reference/en/language/functions/advanced-io/tone/)を翻訳したものです（一部意訳を含みます）

[一覧に戻る](http://pages.nchlab.net/Arduino/ref/)  
[トップページに戻る](http://pages.nchlab.net/)
