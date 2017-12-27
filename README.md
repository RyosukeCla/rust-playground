# My Rust Playground

## setup
```bash
# install rustup
$ curl https://sh.rustup.rs -sSf | sh
$ source $HOME/.cargo/env

# install beta
$ rustup install beta
$ rustup default beta

# rls
$ rustup component add --toolchain=beta rls-preview
$ rustup component add --toolchain=beta rust-src
$ rustup component add --toolchain=beta rust-analysis

```

## Cargo
- `cargo update`: クレートをアップデート。cargo.lockも変わる。
- `cargo run`: run
- `cargo build`: build

## Crate
- 別言語で言うパッケージ、モジュール, ライブラリのこと
- `rand`は外部クレート

## Tutorial
### Guess the number
- `println!("hensu: {}", hensuu)`: よくあるprintln
- `extern create hoge`: 外部crateを宣言
- `use hoge::huga;`: hogeのhugaをuse。from impot as的な
- `extern crate rand; use rand::Rng`: random, `rand::thread_rng().gen_range(1, 101);`
- `let huga = hage`: よくある変数宣言。defaultでimmutable.
- `let mut huga = hage`: mutable
- `io::stdin().read_line(&mut guess)`: return `io::Result instance`
- `io:Result`: のインスタンスは`expect`をもつ。OkとErrをもつ。
- `.expect("test")`: はエラーが起きると、panick!してprocessをkick. そして、messageがはかれる
- `huga.cmp(hage)`: comparableなものに使えるやつ。hugaとhageを比較かな
- `use std::cmp::Ordering;`: enum型. Less, Equal, Greater
- rustは強い型システム。そして型推論もある。
- `shadowing`: `let huga`の後に、`let huga`をできる。新しい定義で隠すことができる。
- `let huga: u32`: でhugaをu32に静的型付け
- `u32`: unsigned 32bit integer
- `guess.trim()`: `\n`とかスペースとかをtrim
- `parse()`: u32とかにparseしてくれる
- `loop`: for loop. break, continue

### Philosopher
- &strは文字列リテラル。Stringとは違う。
- `struct`: 構造体
- `impl`: 実装
- `self`: 明示的に
- `Vec<_>`: _は型プレースホルダ。何らかの型のベクトルだが、型のについてはRustが判断する。
- `into_iter()`: iteratorを作成
- `iterator.map()`: mapにクロージャを渡す
- `|p| {}`: クロージャ？
- `thread::spawn(move || {})`: はクロージャを一つ引数にもつ。新しいスレッドの上でそのクロージャを実行。
- `move`: 上のクロージャは move というアノテーションが必要。キャプチャする値の所有権がクロージャ内へ移動。pが該当。
- `式 vs 文`: セミコロンを付けないと、それはreturnと同じ意味になる。つまり、式。
- `map().collect()`: thread::spawnの返り値つまり、各スレッドへのハンドルをまとめ上げる。
- `join().unwrap()`: 各スレッド実行が終わるまで実行をブロックする。
- `Mutex`: 並行処理を制御するための機構
- `Arc`: Atmic reference count. 複数スレッドからTableを共有するために必要。
- `lock`: eatが終わるまでlockしたいから、`_huga`にlockを保持させてる。eatが終わると、解放されるので。
- `table.clone()`: 参照カウントを増やす。スコープの外にでたときに、カウントが減算される。もし、cloneでカウントを増やさなかったら、いつ解放すればいいのかわからなくなってしまうので、これは必要。
-

## Else
### keybindings.json

```json
// 既定値を上書きするには、このファイル内にキー バインドを挿入します
[{
  "key": "cmd+r",
  "command": "workbench.action.tasks.runTask",
  "args": "cargoRun",
  "when": "editorTextFocus"
}]
```
