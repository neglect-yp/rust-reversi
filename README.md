# Rust でつくるリバーシ

これは Cookpad Spring 1day Internship 2018 Rust プログラミングコースで使用された講義資料です。

設計・模範解答は Rust の特徴的な機能・構文を紹介しやすいように意図的に捻じ曲げてあることがあります。
そのため、必ずしも読みやすい記法ではなかったり、効率的な実装ではなかったりすることがあります。
参考にする際は、以上のことを念頭に入れてお読みください。

## 進め方

各ファイルの `unimplemented!();` を正しい実装で書き換えていくことで進んでいきます。

変更の順序は、まず coord.rs、次に board.rs の順で、それぞれ上から書き換えていきます。

### ドキュメントの開き方

rustdoc という機能により、コード中の構造体やメソッドについてのコメントを読みやすくレンダリングしたドキュメントを生成できます。

ドキュメントを生成するには以下のコマンドを実行します。`--document-private-items` はプライベートな構造体やメソッドについてもドキュメントを生成するためのオプションです。　

```
cargo rustdoc -- --document-private-items
```

レンダリングしたドキュメントは `./taget/doc` 以下に保存されています。

レンダリングしたドキュメントをウェブブラウザで開くためには、次のコマンドが便利です。

```
cargo rustdoc --open -- --document-private-items
```

### テストの実行

各実装がうまく書けているか確かめるため、テストを実行することができます。

全てのテストを実行するには以下のコマンドを実行します。

```
cargo test
```

一部のテストケースのみを実行したい場合はテスト名を付け加えます。例えば、`test_coord_add` を実行したい時には次のようにします。

```
cargo test coord_add
```

テストケースの絞り込みは部分一致のため、この場合は同時に `test_coord_add_assign` も実行されるということに注意してください。

### ゲームの実行

全ての `unimplemented!();` を潰し、全てのテストも通るようになったら、ゲームを起動してみましょう。

ゲームを起動するには次のコマンドを実行します。

```
cargo run
```

これでコンピューターと対戦することができます。

しかし、この状態では Rust のスピードを十分に体感できているとは言えません。なぜならこれはデバッグビルドであり、強力な最適化を施していないプログラムだからです。

Rust のコンパイラの真の力を引き出し、コンピュータプレイヤーの思考速度をざっくり10倍にするには次のコマンドを実行します。

```
cargo run --release
```

ビルド時間は長くなりますが、実行はとても高速になるはずです。

## 各ステップの模範解答の見方

模範解答は [`complete`](https://github.com/KOBA789/rust-reversi/commits/complete) ブランチにあります。

関数単位でコミットを分けてありますので、当該コミットの diff を確認してください。
