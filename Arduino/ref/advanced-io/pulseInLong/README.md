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



# 返り値



# サンプルコード



```cpp

```

# 注意点



# 出典

このページは[Arduino公式のページ](https://www.arduino.cc/reference/en/language/functions/advanced-io/pulseinlong/)を翻訳したものです（一部意訳を含みます）

[一覧に戻る](http://pages.nchlab.net/Arduino/ref/)  
[トップページに戻る](http://pages.nchlab.net/)
