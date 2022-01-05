# TAFuzzer

## 依赖

TAFuzzer运行于Linux系统（Ubuntu 18.04）

环境依赖：

* [CMake](https://cmake.org/download/): 最低版本[3.5.1](sFuzz/CMakeLists.txt#L5)
* [Python](https://www.python.org/downloads/): 最低版本3.5（推荐3.7）
* Go: 推荐版本1.15
* leveldb

## 架构

```shell
$(TAFuzzer)
├── sFuzz
│   ├── fuzzer
│   ├── libfuzzer
│   ├── liboracle
│   └── ...
├── bran
│   └── ...
├── tools
│   ├── requirements.txt
│   └── ...
├── assets
│   ├── ReentrancyAttacker_model.sol
│   ├── ReentrancyAttacker.sol
│   └── ...
├── source_codes
│   └── ...
├── contracts
│   └── ...
├── branch_msg
│   └── ...
├── logs
│   └── ...
├── initial_.sh
├── rename_src.sh
├── run.sh
└── README.md
```

* `sFuzz`；模糊测试工具路径
* `bran`：抽象解释器路径
* `tools`：其它静态工具路径
  * `requirements.txt`：静态工具的python依赖
* `assets`：放攻击合约文件(可自定义)
  * `ReentrancyAttacker_model.sol`：攻击合约模板，可以通过改变中的版本改变生成的攻击合约版本
  * `ReentrancyAttacker.sol`：攻击合约，可以通过模板自动生成，也可以由用户自行定义
* `source_codes`：放待测合约文件（文件名可不需要任何处理）
  * 通过执行rename_src.sh脚本可以自动由该目录下的合约在工作目录下生成文件名符合要求的合约
* `contracts`：工作目录(文件名与合约文件内部的合约名对应一致)
  * 待测合约路径：合约文件名/contract名.sol
  * 检测报告路径：合约文件名/contract名_report.json
* `branch_msg`：存放中间文件
* `logs`：存放运行日志

## 快速开始

初始化及编译：

```bash
./initial_.sh
```

为source_code文件夹内合约建立工作目录：

```bash
./rename_src.sh
```

漏洞检测：

```bash
./run.sh
```

