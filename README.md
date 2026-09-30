# vbox-deps

**vbox 原生二进制依赖托管仓库（D28 决策）**

主仓库 [q2787244398/vboxapp](https://github.com/q2787244398/vboxapp) 不提交原生二进制；
libmpv 等按平台托管在本仓库的 Release 资产，由 `scripts/fetch_libmpv.sh` 下载并随
DMG / EXE 侧载产物分发。

## 资产命名（D28）

```
libmpv-{os}-{arch}-{ver}.{dylib|dll}
libmpv-{os}-{arch}-{ver}.{dylib|dll}.sha256
```

## 当前状态

| 平台 | 资产 | 来源 |
|------|------|------|
| Windows x86_64 | `libmpv-windows-x86_64-0.0.1.dll` | mpv 官方 Windows 构建（shinchiro/mpv-winbuild-cmake），自包含 FFmpeg |
| macOS arm64 | 待制备 | 公开源仅提供静态 `libmpv.a`，无法作为 dylib 分发 |

> 本仓库公开 ⇒ CI 无需额外 secret 即可下载（`fetch_libmpv.sh` 匿名走 Releases API）。
