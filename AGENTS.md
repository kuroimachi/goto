# 项目说明

本项目是 macOS 上使用的单文件 Perl 命令行工具，提供 SSH 主机别名管理、连接测试和 SCP 文件传输。

## 仓库与目录

- 当前项目只有一个 Git 仓库，真实路径为 `/Users/luqiucheng/Code/Machi/github/goto`；`goto` 是主程序。
- 运行时配置位于 `~/Documents/config/goto/goto.ini`，密码使用 macOS Keychain，不属于仓库内容。不要将真实配置或凭证提交到仓库。

## 开发与验证

- 需要 Perl 5.10 或以上及 `Term::ReadKey`；SSH、SCP、Keychain 管理分别依赖系统的 `ssh`、`scp`、`security`。密码认证需要 `sshpass`，SOCKS5 代理需要兼容的 `nc`。
- 可使用 `perl -c goto` 检查语法；实际运行可能创建配置目录、迁移密码或访问远程主机，测试前应确认影响，并避免使用真实凭证。
- 本仓库目前没有独立测试套件或构建流程。修改命令行行为时，应同步检查脚本内帮助信息，并针对相关路径验证。
