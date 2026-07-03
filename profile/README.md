# 奇语言 · Qi Language

> **中文思考,原生速度。** Think in Chinese, run at native speed.
>
> 奇语言不是翻译贴皮——关键字、类型、异常、并发,从源码到机器码全程中文表达,性能与 Go 同场竞技。

**官网 [qilang.org](https://qilang.org)** · [下载 2026.07.03-2](https://github.com/qilang-project/qi/releases/latest) · macOS / Linux / Windows

```qi
包 主程序;

函数 入口() {
    变量 名字: 字符串 = "世界";
    打印行("你好, " + 名字 + "!");
}
```

```bash
qi run 你好.qi      # 编译并运行
qi 运行 你好.qi     # 中文命令等价
```

---

## 项目

| 仓库 | 说明 |
|------|------|
| [qi](https://github.com/qilang-project/qi) | 编译器核心 — LLVM 21 类型化 IR 后端,-O 四档优化,交叉编译 Linux |
| [qi-runtime](https://github.com/qilang-project/qi-runtime) | 运行时(无 LLVM)— ARC 引用计数、M:N 协程调度、标准库 FFI |
| [qi-web](https://github.com/qilang-project/qi-web) | Web 框架 — FastAPI/Express 风格,147k RPS(≈ Go net/http 的 90%) |
| [qi-lsp](https://github.com/qilang-project/qi-lsp) | 语言服务器 — 补全、跳转、诊断、格式化 |
| [qi-vscode](https://github.com/qilang-project/qi-vscode) | VS Code 扩展 — 语法高亮与代码片段 |
| [qi-tools](https://github.com/qilang-project/qi-tools) | 开发工具集 — `qifmt` 格式化(只动空白,绝不毁代码) |
| [qi-test](https://github.com/qilang-project/qi-test) | 测试框架 — 发现并运行 `*_测.qi`,go test 风格 |
| [qi-lang](https://github.com/qilang-project/qi-lang) | AI Agent Skill — 让 Claude 等助手正确读写奇语言(示例全实测) |
| [qi-installer](https://github.com/qilang-project/qi-installer) | 安装器 — macOS pkg / 命令行安装,自带运行时与依赖 |

---

## 语言特性

- **100% 中文关键字** — `如果/否则` `当` `函数` `结构体` `尝试/捕获/最终` `启动` `等待`,中英文标点混用皆可
- **ARC 自动内存管理** — 字符串/结构体/数组/闭包全自动引用计数,默认开启,长跑服务内存有界
- **完整异常机制** — `尝试/捕获/最终/抛出`,协程内异常自动入队,`未来<T>` 出错经 `等待` 传播
- **Go 风格并发** — `启动` 协程、`通道<T>` 通信、M:N 调度
- **包管理** — `qi.toml` + `qi get github.com/user/repo@v1.0`,锁定 commit,编译期零联网
- **原生性能** — LLVM 21 + O3:计算密集与 C/Rust/Go 同梯队(fib(40) 实测快过 Go ~15%)
- **交叉编译** — mac 上一条命令出 Linux 可执行文件(x86_64/aarch64),零 Docker

## 快速开始

```bash
# 下载解压即用(以 macOS Apple Silicon 为例)
curl -LO https://github.com/qilang-project/qi/releases/download/2026.07.03-2/qi-2026.07.03-2-macos-arm64.tar.gz
tar xzf qi-2026.07.03-2-macos-arm64.tar.gz
./bin/qi --version
```

更多:[官网 qilang.org](https://qilang.org) · [语言文档](https://qilang.org/docs/) · [博客](https://qilang.org/blog/)

MIT License · 欢迎 Issue 与 PR
