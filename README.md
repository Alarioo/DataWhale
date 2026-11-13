# 跨平台版本一致性维护
environment.yml手动维护
conda-lock.yml工具生成

| 操作场景 | 命令/步骤 |
|---|---|
| 更新当前环境（按锁文件拉齐版本） | `conda-lock install --name 环境名 conda-lock.yml` |
| 加 conda 包 | 手动更新 `environment.yml` → 重新生成 `conda-lock.yml` |
| 加 pip 包 | 手动更新 `environment.yml` 里 `pip:` 段 → 重新生成 `conda-lock.yml` |
| 删包 | 手动从 `environment.yml` 删一行 → 重新生成 `conda-lock.yml` |
| 升级某个包版本 | 手动更新 `environment.yml` 版本号 → 重新生成 `conda-lock.yml` |
| 清缓存重锁 | `rm -rf /var/folders/*/T/conda-lock-*` → 重跑 |

生成condo-lock：conda-lock --mamba -f environment.yml -p osx-arm64 -p win-64 -p linux-64
