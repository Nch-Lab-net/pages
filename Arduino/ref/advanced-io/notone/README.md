# noTone()

ここは`noTone()` 関数のページです

# 説明

`tone()`によって出力されている矩形波の生成を停止します。トーンが生成されていない場合は何も起こりません

# 構文

`noTone(pin)`

# パラメータ

`pin` :トーンの発生を停止させるArduinoのピン

# 返り値

なし

# 注意点

複数のピンで異なる音程を鳴らしたい場合は、すでに出力しているピンに対し`noTone()`を実行してから、次のピンで`tone()`を呼び出す必要があります。

# 出典

このページは[Arduino公式のページ](https://www.arduino.cc/reference/en/language/functions/advanced-io/notone/)を翻訳したものです（一部意訳を含みます）

[一覧に戻る](https://pages.nchlab.net/Arduino/ref/)  
[トップページに戻る](https://pages.nchlab.net/)
