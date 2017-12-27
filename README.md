# My Rust Playground

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


#### keybindings.json

```json
// 既定値を上書きするには、このファイル内にキー バインドを挿入します
[{
  "key": "cmd+r",
  "command": "workbench.action.tasks.runTask",
  "args": "cargoRun",
  "when": "editorTextFocus"
}]
```
