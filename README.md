# 夸克网盘自动签到

本项目实现了夸克网盘的自动签到功能，通过 GitHub Actions 自动执行，领取每日签到奖励空间，让用户无需手动签到。
本项目基于 `BNDou`大佬的项目中夸克网盘自动签到的子功能 https://github.com/BNDou/Auto_Check_In 修改而来

## 功能简介

- **每日自动签到**：定时运行脚本完成每日签到，领取成长奖励。
- **GitHub Actions 托管**：代码托管在 GitHub 上，设置后每天上午九点自动执行，实现真正的“一劳永逸”。

## 使用指南

### 1. Fork 项目

点击右上角的 `Fork` 按钮，将本项目复制到自己的 GitHub 仓库。

### 2. 配置 Cookie 信息

项目通过 GitHub Secrets 来配置用户的 Cookie 信息。具体步骤如下：

1. **获取 COOKIE_QUARK**

   【手机端】必须使用手机端抓包，小白推荐使用[proxypin](https://github.com/wanghongenpin/proxypin)
   
- 打开抓包工具，手机端访问签到页，

- 找到url为 https://drive-m.quark.cn/1/clouddrive/capacity/growth/info 的请求信息

- 复制url后面的参数: kps sign vcode 粘贴到环境变量

- 环境变量名为 COOKIE_QUARK 多账户用 回车 或 && 分开，例如:（可以直接把你填入的值中的 & 符号替换成 英文分号，不然很容易配错cookie值）

- `user=张三; kps=abcdefg; sign=hijklmn; vcode=111111111;`
> user字段是用户名 (可是随意填写，多账户方便区分)

2. **添加到 GitHub Secrets**
   - 打开你的 Fork 仓库，进入 **Settings -> Secrets and variables -> Actions**。
   - 点击 **New repository secret** 按钮，创建一个名为 `COOKIE_QUARK` 的 Secret。
   - 将刚才配置好的 Cookie 粘贴到值中，保存。

### 3. 启用 GitHub Actions

1. 在你的仓库中，进入 **Actions** 选项卡。
2. 启用 GitHub Actions，会看到 `Quark Sign-in` 工作流已配置完成。
3. 系统会每天自动执行签到脚本，并输出签到结果。

### 4. 手动测试运行

如果想立即测试签到脚本是否配置成功，可以手动触发执行：

1. 进入 **Actions** 选项卡，点击 `Quark Sign-in`。
2. 点击右侧的 **Run workflow**，手动触发一次签到任务，检查是否成功运行。

### 5. 钉钉推送通知

   - 打开你的 Fork 仓库，进入 **Settings -> Secrets and variables -> Actions**。
   - 点击 **New repository secret** 按钮，创建一个名为 `DINGTALK_ACCESS_TOKEN` 的 Secret。
   - 创建钉钉自定义机器人，url中的 `access_token=` 后面的 `xxx` 为值      (注： 没进行加签处理，请创建机器人时选择自定义关键词，并设置关键词为`签到`)

     
### 常见问题

- **签到失败或错误提示**：确认 Cookie 信息准确无误，且格式正确（`user=xxx; kps=xxx; sign=xxx;`）。
- **GitHub Actions 配置未生效**：确认 Fork 项目后，启用 GitHub Actions。

### 注意事项

- 本项目仅用于学习用途，请勿用于非法用途。
- 夸克网盘可能会更新接口或规则，导致签到脚本失效，届时需要重新获取 Cookie 并更新代码。

## 免责声明

本项目为开源学习项目，作者不对项目使用产生的后果负责。使用过程中如有疑问，请参考夸克网盘的官方使用条款。

---

此项目由 GitHub Actions 托管，开放源码，欢迎提交 PR 一起优化！
