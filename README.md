# VS Code 设置同步教程：使用 Sync Settings 插件

本文档将指导您如何使用 **Sync Settings** 插件（由 zokugun 开发），将您的 VS Code 配置（包括设置、快捷键、代码片段、扩展列表等）同步到一个 Git 仓库中，并轻松下载到本地编辑器。

## 第一步：安装插件

1.  打开 VS Code。
2.  进入扩展视图（快捷键 `Ctrl+Shift+X` 或 `Cmd+Shift+X`）。
3.  搜索 `Sync Settings`。
4.  找到由 **zokugun** 开发的插件，点击 **安装**。



## 第二步：配置同步仓库

1.  在 VS Code 中，使用命令面板快捷键 `Ctrl+Shift+P` (Windows/Linux) 或 `Cmd+Shift+P` (Mac)。
2.  输入并选择以下命令：
    > **Sync Settings: Open the repository settings**

3.  这将在编辑器中打开一个名为 `settings.yaml` 的配置文件。将以下配置内容复制到该文件中。

```yaml
# 当前机器名称（可选），可用于过滤设置或在提交信息中使用
hostname: "sunvo-MacBookPro"

# 选择的配置档案名称（必需）
profile: main

# 配置远程 Git 仓库同步
repository:
  # 仓库类型（必需）
  type: git
  # 远程 Git 仓库的 URL（必需）
  url: git@github.com:FerretAngel/vscode-setting-sync.git
  # 要同步的分支名称（可选，默认为 'master'）
  branch: main
```

4.  **重要提示**：请将 `url` 的值替换为您自己的 Git 仓库地址。确保您对该仓库有写入权限。
5.  保存文件 (`Ctrl+S`)。

## 第三步：下载配置（同步到本地）

配置完成后，即可将远程仓库中的设置同步到您的本地 VS Code 编辑器中。

1.  再次打开命令面板 (`Ctrl+Shift+P` / `Cmd+Shift+P`)。
2.  输入并选择以下命令：
    > **Sync Settings: Download (repository -> user)**

3.  插件将自动从您配置的 Git 仓库拉取设置、代码片段、扩展列表等，并应用到当前编辑器。
4.  首次下载时，可能会提示您重启 VS Code 以使某些更改生效。

## 第四步：上传配置（备份到远程）

当您在本机修改了 VS Code 的任何设置、安装了新扩展或创建了新的代码片段后，可以轻松地将这些更改上传备份到远程仓库。

1.  打开命令面板 (`Ctrl+Shift+P` / `Cmd+Shift+P`)。
2.  输入并选择以下命令：
    > **Sync Settings: Upload (user -> repository)**

3.  插件会将您当前的配置状态打包，提交并推送到远程 Git 仓库。

## 命令总结

| 命令 | 功能描述 |
| :--- | :--- |
| **`Sync Settings: Download (repository -> user)`** | 从远程仓库拉取配置，应用到本地编辑器。 |
| **`Sync Settings: Upload (user -> repository)`** | 将本地编辑器的配置推送到远程仓库。 |
| **`Sync Settings: Open the repository settings`** | 打开 `settings.yaml` 配置文件进行编辑。 |

## 温馨提示

*   **SSH 密钥**：如果使用 `git@` 开头的 SSH 地址，请确保您的 SSH 公钥已正确添加到 GitHub 账户。如需使用 HTTPS 方式，只需将 `url` 改为 `https://` 开头即可。
*   **首次使用**：如果您是首次配置，远程仓库可能是空的。直接执行 **Upload** 命令即可完成初始化。
*   **多设备同步**：在其他设备上重复本教程的 **第一步** 到 **第三步**，即可实现跨设备设置同步。

现在，您的 VS Code 设置已经拥有了一个强大而优雅的同步方案！
