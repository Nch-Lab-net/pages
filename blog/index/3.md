# VU-meter を作ってみたけど、、、

<h2><div align="right">2022/06/29</div></h2>

<!-- 記事ここから -->

先日（といっても結構前だけど）、VUメータの基板を発注しました

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">VUメータの基板 <a href="https://t.co/P3gyPOFPk3">pic.twitter.com/P3gyPOFPk3</a></p>&mdash; Nch MOSFET (@Nch_MOSFET) <a href="https://twitter.com/Nch_MOSFET/status/1519659276251242496?ref_src=twsrc%5Etfw">April 28, 2022</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

5mm砲弾型のLED10個をコンパレータとトランジスタでスイッチングさせる、シンプルな回路です

ですが、大きな失敗を2つしていました、、、  
今回はそれについて書き残そうと思います。備忘録兼自戒の念を込めて

## 失敗①｜電源配線を忘れる

「何やってんだ」ってレベルですが、普通にわすれてました

僕が基板設計に使ってるのはKiCADで、実際の画面の一部を切り抜くとこんな感じになってます

<img src="./../../img/VU-meter_circuit.png" alt="" width="75%" border="4">

`U20A`と`U20B`がコンパレータのシンボルです。2回路入なのでAとBに分かれてるんですが、どちらにも電源を繋ぐところがなかったんですよね。だから忘れたんだと思います

対策法はシンボルを作り直すことでなんとかしようと思ってます。詳しくは後日

## 失敗②｜出力方式を間違える

間違えた理由は単純で、データシートをちゃんと見てなかったんですね  
なので、思い込みで作ってました

どういう風に思い込んでたかというと、入力`IN+`と`IN-`を比較した結果を、`H/L`の電圧で出力するという感じです。つまりプッシュプル出力だと思ってた訳です  
ですが、データシートをちゃんと読んでみると、オープンコレクタ出力でした。そりゃ動かんわ（プルアップ抵抗がないためLしか出力できない）

## 失敗は成功のもと

以上を踏まえて、無駄になった基板を供養しつつ再設計する訳ですが、ついでに回路構成も変えようと思ってます

部品点数の削減と実装面積の削減、そしていちばん重要であろうミスを防ぐことが目的です

まず、使用部品について

ほとんどの部品を変更します。詳細は以下の通り。リンクは秋月の販売ページに飛びます

| 部品名 | 変更前 | 個数 | 変更後 | 個数 |
|----|----|----|----|----|
| コンパレータIC | [LM393GN](https://akizukidenshi.com/catalog/g/gI-16987/) | 5 | [NJU7109F](https://akizukidenshi.com/catalog/g/gI-14720/) | 40 |
| 電圧比較用分圧抵抗① | [1/4W 1kΩ](https://akizukidenshi.com/catalog/g/gR-08535/) | 10 | [1608M 1kΩ](https://akizukidenshi.com/catalog/g/gR-11790/) | 40 |
| 電圧比較用分圧抵抗② | [1/4W 20kΩ](https://akizukidenshi.com/catalog/g/gR-08554/) | 10 | [半固定抵抗 200kΩ Bカーブ](https://akizukidenshi.com/catalog/g/gP-14910/) | 2 |
| LED保護抵抗 | [1/4W 510Ω](https://akizukidenshi.com/catalog/g/gR-08533/) | 10 | [1608M 1kΩ](https://akizukidenshi.com/catalog/g/gR-11790/) | 40 |
| LEDドライブ用トランジスタ | [2SC1815](https://akizukidenshi.com/catalog/g/gI-17089/) | 10 | 削減 |  |
| LED | [5mm 砲弾型 青色](https://akizukidenshi.com/catalog/g/gI-01321/) | 10 | [1608M 表面実装型 青色](https://akizukidenshi.com/catalog/g/gI-03982/) | 40 |

見ての通り、数も大きく増やしました。5mm砲弾10個1列から1608M20個2列の構成に変更しています

LEDドライブ用のトランジスタをなくした理由は、使用するコンパレータがプッシュプル出力かつ25mA上限で、計算上5mA以下しか流れない今回の回路では十分な出力を持っているからです

<!-- 記事ここまで -->

<footer><div align="right">©Nch_MOSFET</div></footer>

<!-- 画像を入れる時は
<img src="パス" alt="" width="75%" border="4">
<img src="./../../img/" alt="" width="75%" border="4">
-->

<!-- Twitterのツイートを埋め込むときは公式の埋め込みリンクをそのまま貼るだけで良い -->
