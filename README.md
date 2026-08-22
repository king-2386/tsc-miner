# TensorCash RacerMiner 资源 / TensorCash RacerMiner Resources

这里整理了 RacerMiner 运行所需设备要求、模型下载地址、挖矿软件下载地址、TensorCash 矿池入口、Token 申请、挖矿参数说明、矿机管理系统以及社区交流渠道，方便在 GitHub 自述中快速查看和使用。

This README includes the hardware requirements, model download links, mining software download links, TensorCash pool entry, Worker Token application guide, mining parameters, miner management system, and community links for RacerMiner.

## 设备要求 / Hardware Requirements

- 显卡：大于 10GB 显存的 NVIDIA 显卡
- GPU: NVIDIA GPU with more than 10GB VRAM
- CPU：需支持 AVX2 指令集
- CPU: AVX2 instruction set support is required
- 内存：大于 8GB
- RAM: More than 8GB

## 模型下载 / Model Download

### 国内下载 / Download in China

先安装 ModelScope：

Install ModelScope first:

```bash
pip install modelscope
```

然后下载模型文件：

Then download the model file:

```bash
modelscope download --model RacerModel/Qwen3-8B-Q8_0-full-v2.gguf Qwen3-8B-Q8_0-full-v2.gguf --local_dir ./
```

### 国外下载 / International Download

可以通过 Hugging Face 下载：

You can download the model from Hugging Face:

[Qwen3-8B-Q8_0-full-v2.gguf](https://huggingface.co/buckets/RacerMiner/Qwen3-8B-Q8_0-full-v2.gguf-bucket/resolve/Qwen3-8B-Q8_0-full-v2.gguf?download=true)

## 矿池 / Mining Pool

[TensorCash Tiger Pool](https://tsc-miner.tiger-pool.com/) - 详细挖矿教程请查看矿池。

[TensorCash Tiger Pool](https://tsc-miner.tiger-pool.com/) - Please check the pool page for the detailed mining tutorial.

[申请矿池 Token / 查看挖矿教程](https://tsc-miner.tiger-pool.com/#/start)

[Apply for Pool Token / View Mining Tutorial](https://tsc-miner.tiger-pool.com/#/start)

## Token 申请说明 / Token Application Guide

Token 需要在矿池页面申请，不能随意填写。请先打开 [矿池申请页面](https://tsc-miner.tiger-pool.com/#/start)，填写自己的 TSC 收款地址申请加入矿池，审核通过后在页面获取 Worker Token。

The Worker Token must be applied for on the pool page. Do not fill in a random token. Open the [pool application page](https://tsc-miner.tiger-pool.com/#/start), submit your TSC payout address to apply for pool access, and get your Worker Token after approval.

获取到的 Token 用于矿机连接矿池，请替换配置中的 `（tscp_矿池申请token）` 或 `tscp_你的Token`。请妥善保管 Worker Token，不要泄露给他人。

The Token is used by your miner to connect to the pool. Replace `（tscp_矿池申请token）` or `tscp_你的Token` in the configuration with your own Worker Token. Keep your Worker Token private and do not share it with others.

## 挖矿软件下载 / Mining Software Download

[RacerMiner 挖矿软件下载](https://tsc-miner.tiger-pool.com/) - 请在矿池页面查看并下载最新挖矿软件。

[RacerMiner Mining Software Download](https://tsc-miner.tiger-pool.com/) - Please check the pool page for the latest mining software.

当前参考下载地址：

Current reference download link:

[racer-0.8.4.tar.gz](https://github.com/king-2386/tsc-miner/releases/download/0.8.4/racer-0.8.4.tar.gz)

## 挖矿参数说明 / Mining Parameters

矿池连接地址：

Pool endpoint:

```text
wss://tsc.tiger-pool.com:443/v1/ws
```

Racer 启动参数参考：

Racer startup command example:

```bash
./racer -o wss://tsc.tiger-pool.com:443/v1/ws -u worker_name -a tensorcash --tensorcash-pool-token "tscp_你的Token" --tensorcash-model /hive/miners/custom/Qwen3-8B-Q8_0-full-v2.gguf --tensorcash-pool-difficulty-normalizer 1000000
```

参数说明：

Parameter description:

- `-o`：矿池连接地址，必须保留 `/v1/ws`
- `-o`: Pool endpoint. The `/v1/ws` path must be kept.
- `-u`：矿工名称，可使用字母、数字、点、下划线或连字符
- `-u`: Worker name. Letters, numbers, dots, underscores, and hyphens are supported.
- `-a tensorcash`：挖矿算法 / 网络标识
- `-a tensorcash`: Mining algorithm / network identifier.
- `--tensorcash-pool-token`：矿池 Worker Token，需要在 [矿池申请页面](https://tsc-miner.tiger-pool.com/#/start) 获取
- `--tensorcash-pool-token`: Pool Worker Token. Get it from the [pool application page](https://tsc-miner.tiger-pool.com/#/start).
- `--tensorcash-model`：模型文件路径，请按实际存放位置修改
- `--tensorcash-model`: Model file path. Change it according to your actual model location.
- `--tensorcash-pool-difficulty-normalizer 1000000`：矿池难度归一化参数，保持默认即可
- `--tensorcash-pool-difficulty-normalizer 1000000`: Pool difficulty normalizer. Keep the default value.

多显卡可按实际情况增加 GPU 参数，例如：

For multiple GPUs, add GPU parameters as needed, for example:

```bash
--gpu "0,1,2,3,4" --tensorcash-gpu-groups "0;1;2;3;4"
```

如果启动时报错包含 `/libggml-cpu.so.0: libgomp.so.1`，可安装依赖：

If the startup error contains `/libggml-cpu.so.0: libgomp.so.1`, install the dependency:

```bash
apt update
apt install -y libgomp1
```

## 矿机管理系统 / Miner Management System

[MinerOS](https://mineros.net/)

## HiveOS / MinerOS 通用飞行表 / HiveOS / MinerOS Universal Flight Sheet

导入飞行表后，请将 `（tscp_矿池申请token）` 替换为自己在 [矿池申请页面](https://tsc-miner.tiger-pool.com/#/start) 获取的 token。模型文件需放在 `/hive/miners/custom/Qwen3-8B-Q8_0-full-v2.gguf`，或按实际存放路径修改 `--tensorcash-model`。

After importing the flight sheet, replace `（tscp_矿池申请token）` with the token you obtained from the [pool application page](https://tsc-miner.tiger-pool.com/#/start). The model file should be placed at `/hive/miners/custom/Qwen3-8B-Q8_0-full-v2.gguf`, or you can update `--tensorcash-model` to match your actual path.

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
        "install_url": "https://github.com/king-2386/tsc-miner/releases/download/0.8.4/racer-0.8.4.tar.gz",
        "user_config": "-a tensorcash\n--tensorcash-pool-token （tscp_矿池申请token）\n--tensorcash-model /hive/miners/custom/Qwen3-8B-Q8_0-full-v2.gguf\n--tensorcash-pool-difficulty-normalizer 1000000"
      },
      "pool_geo": []
    }
  ]
}
```
<img width="678" height="818" alt="image" src="https://github.com/user-attachments/assets/c2f1b17e-2a68-4284-a37c-f7546b582f14" />
## 社区交流 / Community

- Discord: [https://discord.gg/3nZmxtm4Pg](https://discord.gg/3nZmxtm4Pg) - 意见及帮助请联系 DC 群管理。
- Discord: [https://discord.gg/3nZmxtm4Pg](https://discord.gg/3nZmxtm4Pg) - For feedback or support, please contact the Discord group admins.
- Telegram: [https://t.me/+D84HNY1Ct8AyNjRk](https://t.me/+D84HNY1Ct8AyNjRk) - 意见及帮助请联系 TG 群管理。
- Telegram: [https://t.me/+D84HNY1Ct8AyNjRk](https://t.me/+D84HNY1Ct8AyNjRk) - For feedback or support, please contact the Telegram group admins.
