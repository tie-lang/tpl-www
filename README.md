# TPL Website / TPL 官网

The official website for the **Tie Public License (TPL)**, styled after the
minimalist tradition of llvm.org: pure hand-written HTML + a single CSS file,
no frameworks, no build system, no client-side JavaScript.

**Tie Public License（TPL）官方网站**，风格效仿 llvm.org 的极简传统：纯手写
HTML + 单个 CSS 文件，无框架、无构建系统、无客户端 JavaScript。

## Layout / 目录结构

```
tools/       license page generator (pure tie) / 许可证页面生成器（纯 tie）
assets/      site.css / 站点样式
en/          English pages (canonical) / 英文页面（为准版本）
zh/          Chinese mirror / 中文镜像
nginx/       server config: Accept-Language negotiation / 服务器配置：语言协商
```

## Pages / 页面

| Path | Content / 内容 |
|------|----------------|
| `/` | nginx 302 by `Accept-Language`, cookie overrides / 按语言头跳转，cookie 优先 |
| `en/` `zh/` | Home: what TPL is, principles, version table / 首页 |
| `en/2.2/` `en/2.1/` `en/2.0/` | Full license text with section anchors / 许可证全文（§ 锚点） |
| `en/using/` | How to apply TPL to your project / 如何采用 TPL |
| `en/faq/` | Frequently asked questions / 常见问题 |

## Single source of truth / 文本单一来源

All license page HTML is **generated** from the `tie-lang/TPL` repository
(`tpl.txt`, `2.2`, `2.1`, `2.0`) by `tools/gen_lic.tie`. Never hand-edit the
generated pages — edit the TPL repo, then regenerate. On a version bump:
update the TPL repo (dual-write `tpl.txt` + versioned copy), then re-run the
generator.

所有许可证页面的 HTML 均由 `tools/gen_lic.tie` 从 `tie-lang/TPL` 仓的
`tpl.txt` / `2.2` / `2.1` / `2.0` **生成**。禁止手改生成页——改 TPL 仓后重新
生成。换版流程：TPL 仓双写（`tpl.txt` + 版本号副本）→ 重跑生成器。

```sh
cd tools
tiec --no-cache gen_lic.tie
./gen_lic.exe
```

## Language policy / 语言策略

English is the authoritative language. Untranslated pages fall back to English
with a banner. The server negotiates the initial language via the
`Accept-Language` header; the manual switcher stores a preference cookie that
takes priority over header negotiation.

英文为准。未翻译页回落英文并显示横幅说明。初始语言由服务端按
`Accept-Language` 协商；手动切换写入偏好 cookie，cookie 优先于请求头。

## License / 许可证

The repository text is the Tie Public License 2.2. The website itself is
published under the TPL 2.2, © TIE-LANG organization.

本仓文本即 TPL 2.2；网站本身以 TPL 2.2 发布，© TIE-LANG organization。
