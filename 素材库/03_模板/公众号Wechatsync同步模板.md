# 公众号 Wechatsync 同步模板

> 用途：把公众号文章统一写成 Markdown 源文件，再通过 Wechatsync 同步到微信公众号草稿箱。

## 使用前提

- Chrome 已安装 Wechatsync 扩展。
- Chrome 已登录微信公众号后台。
- Wechatsync 扩展里已开启同步/桥接能力，并设置 token。
- 本机已安装 CLI：`@wechatsync/cli`。
- PowerShell 当前会话已设置：`WECHATSYNC_TOKEN`。

## 推荐存放位置

```text
素材库/02_内容项目/公众号/YYYY-MM-DD_主题/article.md
```

示例：

```text
素材库/02_内容项目/公众号/2026-06-25_第13期匹配预告/article.md
```

## 文章源文件格式

```md
# 标题

> 摘要：一句话说明这篇文章要表达什么。

## 开头

正文。

## 核心内容

正文。

## 行动引导

正文。

---

哈喽Hello  
每周一 / 周四 20:00 同频匹配
```

## 同步前检查

```powershell
$env:WECHATSYNC_TOKEN="你的token"
wechatsync platforms --auth
```

确认 `weixin` 已登录后，再同步。

## 同步到公众号草稿

```powershell
wechatsync sync "E:\about_hello\素材库\02_内容项目\公众号\YYYY-MM-DD_主题\article.md" -p weixin
```

## 多平台同步

如同一篇内容也要同步到小红书、抖音图文，可用：

```powershell
wechatsync sync "E:\about_hello\素材库\02_内容项目\公众号\YYYY-MM-DD_主题\article.md" -p weixin,xiaohongshu,douyin
```

## 注意事项

- Wechatsync 更适合“同步草稿”，最终发布前仍建议在公众号后台预览和微调。
- 公众号复杂排版不要只依赖 Markdown，封面、摘要、图片位置需要人工确认。
- 不要把 token 写进仓库文件，只在本机环境变量里设置。
