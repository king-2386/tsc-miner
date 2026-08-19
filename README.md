# TensorCash RacerMiner 资源

这里整理了 RacerMiner 运行所需设备要求、模型下载地址、挖矿软件下载地址、TensorCash 矿池入口、矿机管理系统以及社区交流渠道，方便在 GitHub 自述中快速查看和使用。

## 设备要求

- 显卡：大于 10GB 显存的 NVIDIA 显卡
- CPU：需支持 AVX2 指令集
- 内存：大于 8GB

## 模型下载

### 国内下载

先安装 ModelScope：

```bash
pip install modelscope
```

然后下载模型文件：

```bash
modelscope download --model RacerModel/Qwen3-8B-Q8_0-full-v2.gguf Qwen3-8B-Q8_0-full-v2.gguf --local_dir ./
```

### 国外下载

可以通过 Hugging Face 下载：

[Qwen3-8B-Q8_0-full-v2.gguf](https://huggingface.co/RacerMiner/Qwen3-8B-Q8_0-full-v2.gguf/resolve/main/Qwen3-8B-Q8_0-full-v2.gguf?download=true)

## 矿池

[TensorCash Tiger Pool](https://tsc-miner.tiger-pool.com/) - 详细挖矿教程请查看矿池。

## 挖矿软件下载

[RacerMiner 挖矿软件下载](https://tsc-miner.tiger-pool.com/) - 请在矿池页面查看并下载最新挖矿软件。

## 矿机管理系统

[MinerOS](https://mineros.net/)

## HiveOS / MinerOS 通用飞行表

导入飞行表后，请将 `（tscp_矿池申请token）` 替换为自己在矿池申请的 token。模型文件需放在 `/hive/miners/custom/Qwen3-8B-Q8_0-full-v2.gguf`，或按实际存放路径修改 `--tensorcash-model`。

```json
{
  "name": "TSC",
  "isFavorite": false,
  "items": [
    {
      "coin": "tsc",
      "pool_ssl": false,
      "wal_id": 11124400,
      "dpool_ssl": false,
      "miner": "custom",
      "miner_alt": "racer",
      "miner_config": {
        "url": "wss://tsc.tiger-pool.com:443/v1/ws",
        "miner": "racer",
        "template": "%WORKER_NAME%",
        "install_url": "https://github.com/king-2386/tsc-miner/releases/download/tsc/racer-0.8.2.tar.gz",
        "user_config": "-a tensorcash\n--tensorcash-pool-token （tscp_矿池申请token）\n--tensorcash-model /hive/miners/custom/Qwen3-8B-Q8_0-full-v2.gguf\n--tensorcash-pool-difficulty-normalizer 1000000"
      },
      "pool_geo": []
    }
  ]
}
```
<img width="678" height="818" alt="image" src="https://github.com/user-attachments/assets/c2f1b17e-2a68-4284-a37c-f7546b582f14" />



## 社区交流

- Discord: [https://discord.gg/3nZmxtm4Pg](https://discord.gg/3nZmxtm4Pg) - 意见及帮助请联系 DC 群管理。
- Telegram: [https://t.me/+D84HNY1Ct8AyNjRk](https://t.me/+D84HNY1Ct8AyNjRk) - 意见及帮助请联系 TG 群管理。
