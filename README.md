# IIA 科目三网页

计划公开仓库：h2-ops/iiaproject3-web。
计划GitHub Pages地址：`https://h2-ops.github.io/iiaproject3-web/`，需以Pages发布成功结果为准。

这是纯静态网页程序，不包含题库、答案、解析数据、原工作簿、个人进度或访问凭据。它从独立私有仓库 `h2-ops/iiaproject3` 读取题库和同步进度。

## 发布

在GitHub创建同名Public空仓库，推送本目录的独立Git历史。仓库Settings → Pages → Source选择Deploy from a branch，Branch选择main，Folder选择/(root)，保存。无需构建或ChatGPT账号。

不要将原私有仓库改公开或将其Git历史推入本仓库：原私有历史包含题库资料。此目录建立的是全新Git历史。

## Token接入

1. 在GitHub创建fine-grained personal access token。
2. Resource owner选择h2-ops；Repository access选择Only select repositories，**只授权私有仓库iiaproject3**。
3. Repository permissions的Contents设为Read and write，选择适当到期时间。
4. 打开网页，将token粘贴到连接表单。仅在自己的网页中输入，不放入代码、提交、聊天或README。
5. 网页会读取 `data/cia3-questions.json`，并将进度写入 `data/cia3-progress.json`。

Token保存在当前浏览器localStorage，可在网页断开连接并删除。公开源码里不含token。多设备使用同一私有仓库时共享一份学习进度。也可导入本地题库，不使用token。

题库保留1389题、185道带标签AI解析和10道待复核意见；数据只存在私有仓库或导入后的本机缓存中。

## 迁移旧进度

先在旧网页导出学习进度，在新网页连接题库后导入。稳定题目ID不变；新站不自动读取其他域名的数据。

## 已验证

无token时不发网络请求；无效token不保存；超过1MB题库可通过GitHub原文接口读取；UTF-8笔记同步；409冲突后重新合并；断开连接清除token但保留本机题库和记录。上述为网络模拟与本地自动检查，真实联网和Pages上线须在远程仓库建立后继续验证。
