Reverse engineering and low-level systems. I spend most of my time below the line where the public API stops — macOS internals, Mach-O and arm64, wire protocols — in C, Rust and Python.

Three things that show what that means in practice:

- [**macos-360hz-unlock**](https://github.com/owomocha/macos-360hz-unlock) — my monitor does 360 Hz, macOS capped it at 300. The display coprocessor turned out to drop any mode whose vertical blanking *time* is too short, so I hand it an EDID with fatter blanking through two private IOKit calls I recovered from the dyld shared cache. 60 Hz back, no extra hardware, vsync counted at 359.998.
- [**protocol-rekit**](https://github.com/owomocha/protocol-rekit) — reading how a closed desktop app talks to its server when the traffic is cleartext. A pcap/pcapng parser, arm64 adrp/add string recovery, a findcrypt-style constant scanner, and a way to tell a live feed from a replayed one by timing. Standard library only: no scapy, no capstone.
- [**hidden-1s-candles**](https://github.com/owomocha/hidden-1s-candles) — which exchanges actually serve 1-second candles, measured across 22 of them with a control beside every "no". Eight do; only two say so in their docs.

The common thread is that I don't take the docs' word for it. Measure, put a control next to every claim, and write down the times I got it wrong.

Currently: a Rust video editor and a wgpu charting app on Apple Silicon. Getting the parts I can share into public shape.

---

低レイヤーとリバースエンジニアリングが中心です。公開 API が終わるところから下 — macOS の内部、Mach-O / arm64、通信プロトコル — を C・Rust・Python でやっています。上の 3 つが具体例で、共通しているのは「ドキュメントを信じず実測する。主張のそばに必ず対照を置く。間違えた回数も書く」こと。いまは Apple Silicon 上の Rust 製動画エディタと wgpu チャートを、出せる部分から公開できる形に整えています。
