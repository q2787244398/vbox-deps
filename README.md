# vbox-deps

**vbox 原生二进制依赖托管仓库（D28 决策）**

主仓库 [q2787244398/vboxapp](https://github.com/q2787244398/vboxapp) 不提交原生二进制；
libmpv 等按平台托管在本仓库的 Release 资产，由 `scripts/fetch_libmpv.sh` 下载并随
DMG / EXE 侧载产物分发。

## 资产命名（D28）

```
# Windows：单一自包含 dll
libmpv-windows-{arch}-{ver}.dll
libmpv-windows-{arch}-{ver}.dll.sha256

# macOS：动态库集合（libmpv.dylib + @rpath 依赖 dylib，整组随 App Frameworks 分发）
libmpv-macos-{arch}-{ver}.tar.gz
libmpv-macos-{arch}-{ver}.tar.gz.sha256
```

## 当前状态

| 平台 | 资产 | 来源 |
|------|------|------|
| Windows x86_64 | `libmpv-windows-x86_64-0.0.1.dll` | mpv 官方 Windows 构建（shinchiro/mpv-winbuild-cmake），自包含 FFmpeg |
| macOS arm64 | `libmpv-macos-arm64-0.0.1.tar.gz`（18 个 dylib） | media_kit [libmpv-darwin-build](https://github.com/media-kit/libmpv-darwin-build) v0.7.3 `macos-arm64-video-default`（LGPL） |

> 本仓库公开 ⇒ CI 无需额外 secret 即可下载（`fetch_libmpv.sh` 匿名走 Releases API）。
> SHA256 同步登记于主仓库 `scripts/libmpv_external_dependencies.json`。
