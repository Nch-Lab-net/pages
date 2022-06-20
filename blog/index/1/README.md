# ふつくしい配線は良いというおはなし

## <div align="right">2022/06/20</div>

先日とある事情で研究所に行って色々やってました  
その時に息抜きに作った回路が割と好評だったので、Twitterにも上げたものですがここにも残します

まずはｵｼｬｼﾝをば

<img src="./../../img/FVlu4h7VIAAQq5N.jpeg" alt="円形基板に施した配線" width="75%" border="4">

<img src="./../../img/IMG_7826.JPG" alt="立体配線で作った非安定マルチバイブレータ" width="75%" border="4">

ツイートはこちら

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">後輩に「工作精度おかしいやろ」と言われた配線 <a href="https://t.co/kgN8hW5wgA">pic.twitter.com/kgN8hW5wgA</a></p>&mdash; Nch MOSFET (@Nch_MOSFET) <a href="https://twitter.com/Nch_MOSFET/status/1538382678977761281?ref_src=twsrc%5Etfw">June 19, 2022</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">デキタ <a href="https://t.co/LFFrRKfJNv">https://t.co/LFFrRKfJNv</a> <a href="https://t.co/LrNIWxsu4b">pic.twitter.com/LrNIWxsu4b</a></p>&mdash; Nch MOSFET (@Nch_MOSFET) <a href="https://twitter.com/Nch_MOSFET/status/1538414009329647616?ref_src=twsrc%5Etfw">June 19, 2022</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

どうです？　めちゃくちゃ良くないですか？　（自画自賛）

一枚目はArduino Nanoを載せる基板、二枚目は立体配線で作った非安定マルチバイブレータです  
直線・直角配線こそ至高。これは何度でも唱えていきたい

二枚目のバイブレータの動作、ちゃんと動いてくれてますね

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">新幹線の中で発振回路を発振させてます（非安定マルチバイブレータ） <a href="https://t.co/HD19oLQPBm">pic.twitter.com/HD19oLQPBm</a></p>&mdash; 溶けかけてるうさぎ (@_meltingrabbit) <a href="https://twitter.com/_meltingrabbit/status/1538494111967170561?ref_src=twsrc%5Etfw">June 19, 2022</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

回路定数ですが、コンデンサの＋側とLEDに繋がっている抵抗が4.7kΩ、コンデンサのー側に繋がっている抵抗が82kΩ、コンデンサ容量が10μF、トランジスタは2SC1815、電源電圧は9Vです（006P）  
この通りに作ると遮断器の信号みたいな光り方をします

僕も新幹線で発振回路動かしたい、けど新幹線に乗る機会が _nothing_
