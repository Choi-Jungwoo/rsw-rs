<p align="center">
  <img src="./rsw.png" width="120">
</p>

「🌐 语言」[English](./README.md)

## rsw-rs

## 用法

```bash
# 安装
cargo install rsw
```

```bash
# 查看帮助
rsw -h

# 开发模式
rsw watch

# 生产构建
rsw build
```

## rsw.toml

> 配置文件

在项目根路径下创建 `rsw.toml`，配置 `rust crate` 参数，然后执行 `rsw watch` 或者 `rsw build`。

- **`name`** - 配置文件名称（无意义，可选）
- **`version`** - 配置文件版本（无意义，可选）
- **`interval`** - 开发模式 `rsw watch` 下，文件变更触发 `wasm-pack build` 的时间间隔，默认 `50` 毫秒
- **`[[crates]]`** - 数组，支持多个 `rust crate` 配置
  - **`name`** - npm 包名，支持组织，例如 `@rsw/foo`
  - **`root`** - 当前 `rust crate` 所在目录，默认 `.`
  - **`out-dir`** - wasm 文件输出路径，默认 `pkg`
  - **`[crates.watch]`** - 监听模式下的配置
    - **`run`** - 是否执行，默认为 `true`
    - **`profile`** - `dev` | `profiling`，默认 `dev`
  - **`watch`** - 生产构建下的配置
    - **`run`** - 是否执行，默认为 `true`
    - **`profile`** - `release` | `profiling`，默认 `release`

了解更多 [wasm-pack build](https://rustwasm.github.io/docs/wasm-pack/commands/build.html)

```toml
name = 'rsw'
version = "0.0.1"
interval = 50

[[crates]]
root = "."
name = "rsw-foo"
# out-dir = "./mypkg"
# profile: dev | profiling, defalut `dev`
[crates.watch]
run = true
profile = "dev"
# profile: release | profiling, default `release`
[crates.build]
run = false
profile = "profiling"

[[crates]]
name = "@rsw/bar"
```

## License

MIT License © 2022 lencx
