# Duolingo

[![维持我的Duolingo连胜](https://github.com/fywmjj/dlg/actions/workflows/streak-keeper.yml/badge.svg?branch=main)](https://github.com/fywmjj/dlg/actions/workflows/streak-keeper.yml)

:important:
本仓库不是原版仓库，要Fork，请到[此处](https://github.com/rfoel/duolingo/fork)克隆原版Duolingo仓库。

<img src="duo.svg" width="128px"/>

用于Duolingo的连胜维持工具及经验积累辅助。再也不担心被降级了！

### 使用指南

1. [克隆本仓库](https://github.com/rfoel/duolingo/fork)
2. 访问 [Duolingo网站](https://www.duolingo.com)
3. 登录后，打开浏览器的控制台（Mac用户按Option (⌥) + Command (⌘) + J，Windows/Linux用户按Shift + CTRL + J）
4. 在控制台执行以下脚本获取JWT令牌，并复制其值（确保不包括引号）

```js
document.cookie
  .split(';')
  .find(cookie => cookie.includes('jwt_token'))
  .split('=')[1]
 ```

5. 回到你克隆的仓库页面
6. 进入设置页面，选择 Secrets and Variables > Actions，点击 `New Repository secret` 按钮
7. 密钥名称填写 `DUOLINGO_JWT`，密钥值填写上一步获得的JWT令牌值
8. 返回仓库页面，进入 Actions 选项卡，点击 `I understand my workflows, go ahead and enable them`

## 工作流说明

### 🔥 连胜维持

本项目通过定时的 GitHub Actions 工作流来帮助用户维持Duolingo的连胜记录。工作流的详情可查阅 [这里](.github/workflows/streak-keeper.yml)。

### 📚 自动学习

此仓库还能帮助自动完成课程学习，为您积累经验，避免等级下降。使用 [workflow_dispatch](https://docs.github.com/actions/using-workflows/events-that-trigger-workflows#workflow_dispatch) 触发学习任务，您可以自定义完成的课程数量。具体工作流详情请参见 [这里](.github/workflows/study.yml)。

## 使用须知

- 该工具不支持完成每日任务或好友挑战，只能帮助积累经验，提升联赛排名；
- 该工具不会参与真实的课程或故事学习，只进行练习，不影响您的学习进度；

## 独立运行脚本

若希望在GitHub以外运行本脚本，您可以创建一个包含 `DUOLINGO_JWT` 的 `.env` 文件，按以下方式执行脚本：

```
node --env-file=.env index.js
```

> 运行此脚本需要 Node v20.6.0 或更高版本。

也可以在终端直接设置环境变量后运行：

```
DUOLINGO_JWT=... node index.js
```
