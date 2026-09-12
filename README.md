I'm a security engineer. I reverse-engineer things and work close to the metal: a display controller's private interface, the instruction stream inside a Mach-O, a closed app's wire protocol. Mostly on macOS, in C, Rust and Python.

Some of my work:

- [macos-360hz-unlock](https://github.com/owomocha/macos-360hz-unlock). My monitor does 360 Hz and macOS would only give me 300. The display coprocessor turns out to reject any mode whose vertical blanking is shorter than about 100–150 µs, so I hand it an EDID with fatter blanking through two private IOKit calls (selectors dug out of the dyld shared cache) and make it rebuild its timing table. Counted vsyncs afterwards: 359.998 Hz.
- [protocol-rekit](https://github.com/owomocha/protocol-rekit). Reading a closed desktop app's traffic when it's in the clear: pcap parser, arm64 string recovery, crypto-constant scanner. Standard library only.
- [hidden-1s-candles](https://github.com/owomocha/hidden-1s-candles). Which exchanges actually serve one-second candles. 22 tested, 8 do, and 6 of those never say so.

[Browse all repositories](https://github.com/owomocha?tab=repositories).

My work also includes a GPU video compositor and a real-time charting engine, both Rust on Apple silicon, reversing closed runtimes and the anti-tamper wrapped around them, and fuzzers pointed at file-format parsers, where the memory-corruption bugs tend to live.

I don't trust documentation. I measure the thing, keep a control next to every claim, and write down the times I was wrong.

---

セキュリティエンジニアです。リバースエンジニアリングと低レイヤーが中心です。ディスプレイコントローラの非公開インターフェース、Mach-O の中の命令列、クローズドなアプリの通信プロトコル。だいたい macOS 上で、C・Rust・Python で書いています。

手がけたプロジェクトの一部です。

- [macos-360hz-unlock](https://github.com/owomocha/macos-360hz-unlock)。360 Hz のモニタを macOS が 300 までしか出してくれなかった話。ディスプレイコプロセッサは垂直ブランキングが 100〜150 µs より短いモードを捨てていたので、ブランキングを太らせた EDID を非公開の IOKit 呼び出し 2 本（セレクタは dyld 共有キャッシュから掘り出した）で渡し、タイミング表を作り直させる。あとで vsync を数えたら 359.998 Hz。
- [protocol-rekit](https://github.com/owomocha/protocol-rekit)。平文で喋るクローズドなデスクトップアプリの通信を読む道具。pcap パーサ、arm64 の文字列復元、暗号定数スキャナ。標準ライブラリだけ。
- [hidden-1s-candles](https://github.com/owomocha/hidden-1s-candles)。本当に 1 秒足を配信している取引所はどこか。22 か所を試して 8 か所、うち 6 か所はどこにも書いていない。

[リポジトリ一覧を見る](https://github.com/owomocha?tab=repositories)。

ほかにも、Rust と Apple silicon で GPU 動画コンポジタとリアルタイムのチャートエンジンを書いたり、クローズドなランタイムと耐タンパ保護を解析したり、ファイルフォーマットのパーサに自作ファザーを向けたりしています。面白いメモリ破壊バグはたいていそこにあるので。

ドキュメントは信用しません。自分で測って、主張の隣に対照を置いて、間違えた回数を書き残す。
