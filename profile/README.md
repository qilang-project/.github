# 奇语言 · Qi Language

> **中文思考，原生速度。** Think in Chinese, run at native speed.
>
> 关键字、类型、异常、并发，从源码到机器码全程中文表达。编译出来是一个原生可执行文件，
> 性能与 Go 同场竞技。

**官网 [qilang.org](https://qilang.org)** · **包中心 [pkg.qilang.org](https://pkg.qilang.org)** · [下载 2026.08.16-2](https://github.com/qilang-project/qi/releases/latest) · macOS / Linux / Windows

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

编译器、运行时、语言服务器、图形库是 Rust 写的；Web、CLI、Agent、RPC、测试框架
都是**用奇语自己写的**。

| 仓库 | 说明 |
|------|------|
| [qi](https://github.com/qilang-project/qi) | 编译器核心 — LLVM 21 类型化 IR 后端，-O 四档优化，交叉编译 Linux/Windows |
| [qi-runtime](https://github.com/qilang-project/qi-runtime) | 运行时（无 LLVM）— ARC 引用计数、协程调度、标准库 FFI |
| [qi-web](https://github.com/qilang-project/qi-web) | Web 框架 — FastAPI/Express 风格，实测 ~122k RPS，含 LiveView 实时页面 |
| [qi-cli](https://github.com/qilang-project/qi-cli) | CLI 框架 — Cobra 风格命令树、子命令、持久参数、执行钩子 |
| [qi-harness](https://github.com/qilang-project/qi-harness) | LLM Agent 框架 — 可观测/可重试/可评估，流式与并行工具调用 |
| [qi-grpc](https://github.com/qilang-project/qi-grpc) | gRPC — 一元/流式、TLS、gzip、服务反射，与 Go 实测互通 |
| [qi-lsp](https://github.com/qilang-project/qi-lsp) | 语言服务器 — 补全、跳转、诊断、格式化 |
| [qi-vscode](https://github.com/qilang-project/qi-vscode) | VS Code 扩展 — 语法高亮与代码片段 |
| [qi-gui](https://github.com/qilang-project/qi-gui) | 图形库 — winit + softbuffer 软件渲染（不依赖 GPU）+ egui 控件与 2D 画布 |
| [qi-tools](https://github.com/qilang-project/qi-tools) | 开发工具集 — `qifmt` 格式化（只动空白，绝不毁代码） |
| [qi-test](https://github.com/qilang-project/qi-test) | 测试框架 — 发现并运行 `*_测.qi`，go test 风格 |
| [qi-lang](https://github.com/qilang-project/qi-lang) | AI Agent Skill — 让 Claude 等助手正确读写奇语言（示例全实测） |
| [qi-installer](https://github.com/qilang-project/qi-installer) | 安装器 — macOS `.pkg` / Windows `.msi` / 命令行安装，自带运行时 |

---

## 语言特性

- **100% 中文关键字** — `如果/否则` `当` `函数` `结构体` `尝试/捕获/最终` `启动` `等待`，中英文标点混用皆可
- **ARC 自动内存管理** — 字符串/结构体/数组/闭包全自动引用计数，默认开启，长跑服务内存有界
- **完整异常机制** — `尝试/捕获/最终/抛出`，协程内异常自动入队，`未来<T>` 出错经 `等待` 传播
- **Go 风格并发** — `启动` 协程、`通道<T>` 通信，一个线程池跑成千上万个协程
- **包管理** — 注册中心 [pkg.qilang.org](https://pkg.qilang.org)（`qi 包 添加/发布/搜索`，sha256 + 锁文件），或 `qi get github.com/user/repo@v1.0` 直接从 git 取
- **原生性能** — LLVM 21 + O3：计算密集与 C/Rust/Go 同梯队
- **交叉编译** — mac 上一条命令出 Linux 可执行文件（x86_64/aarch64），零 Docker
- **C 互通** — `外部` 块直接调 C 库，`qi 绑定` 从头文件自动生成绑定；DWARF 调试信息可在 lldb 里按中文源码断点

## 快速开始

```bash
# 一键安装（macOS / Linux）：装好编译器与运行时，并真编译一个程序验证
curl -fsSL https://raw.githubusercontent.com/qilang-project/qi/main/scripts/install.sh | bash

# 写第一个程序
echo '包 主程序; 函数 入口() { 打印行("你好, 世界!"); }' > 你好.qi
qi run 你好.qi
```

Windows 用 [Releases](https://github.com/qilang-project/qi/releases/latest) 里的 `.zip`
或 qi-installer 的 `.msi`。

更多：[官网 qilang.org](https://qilang.org) · [语言文档](https://qilang.org/docs/) · [博客](https://qilang.org/blog/) · [包中心](https://pkg.qilang.org)

MIT License · 欢迎 Issue 与 PR
