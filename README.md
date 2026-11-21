# goto

macOS 上的 SSH 主机管理和 SCP 文件传输工具。

## 依赖与启动

需要 Perl 5.10 或以上、`Term::ReadKey`、`ssh`、`scp` 和 macOS `security`。密码认证需要 `sshpass`，SOCKS5 代理需要支持 `-x` 的 `nc`。确保 `goto` 可执行，并将所在目录加入 `PATH`，或者在仓库目录使用 `./goto`。

直接运行 `goto` 打开交互菜单，用方向键选择、回车确认，按 `q` 退出。首次使用可通过「管理主机」新增主机。主机信息保存在 `~/Documents/config/goto/goto.ini`，密码保存在 macOS Keychain，勿将真实配置或凭证提交到仓库。

## 命令

```bash
goto server1                         # 连接主机
goto ssh server1                     # 显式连接主机
goto up server1 ./local /remote      # 上传
goto down server1 /remote ./local    # 下载
goto test server1                    # 测试连接
goto ping server1                    # Ping
goto list                            # 列出主机
goto edit                            # 编辑配置
goto delete server1                  # 删除主机（需要确认）
goto help                            # 查看帮助
```

缺少主机或传输路径时，程序会在交互终端提示选择或输入。子命令优先于同名主机别名；例如，使用 `goto ssh up` 连接名为 `up` 的主机。旧的 `--list` 等功能选项不再支持。

`-x` 或 `--proxy` 启用 SOCKS5 代理，`-r` 或 `--recursive` 递归传输，`-q` 或 `--quiet` 抑制连接测试的实时输出。代理默认地址为 `127.0.0.1:7890`，可在配置文件的 `[global]` 中使用 `proxy_host` 和 `proxy_port` 修改。无 Keychain 密码时，SSH 登录提示输入密码；留空可使用 SSH 密钥。
