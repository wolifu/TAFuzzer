# TAFuzzer

An effective and efficient targeted fuzzing framework for smart contract vulnerability detection.


## Requirements

TAFuzzer is supported on Linux (ideally Ubuntu 18.04).

Dependencies: 

* [CMake](https://cmake.org/download/): >=[3.5.1](sFuzz/CMakeLists.txt#L5)
* [Python](https://www.python.org/downloads/): >=3.5（ideally 3.6）
* Go: 1.15
* leveldb

## Architecture

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

* `sFuzz`: fuzzing tool of our TAFuzzer
* `bran`: abstract interpreter
* `tools`: other static analysis tools
  * `requirements.txt`：python dependecies
* `assets`:
  * `ReentrancyAttacker_model.sol`: template for attacker contract
  * `ReentrancyAttacker.sol`: an attacker contract generated based on th template
* `source_codes`：restore the contracts under test
  * rename_src.sh is used to produce the required contract name
* `contracts`: 
  * contract under test: contract_name/contract_name.sol
  * fuzzing log: contract_name/contract_name_report.json
* `branch_msg`：restore the 
* `logs`：fuzzing execution report

## Quick Start

- Initialization and Install system dependencies

```bash
./initial_.sh
```

- Make workspace for directory of source codes

```bash
./rename_src.sh
```

- Run TAFuzzer and perform vulnerability detection

```bash
./run.sh
```

- The code is adapted from [sFuzz](https://github.com/duytai/sFuzz) (a state-of-the-art fuzzer for smart contracts) and [bran](https://github.com/Practical-Formal-Methods/bran) (a static analysis framework for EVM bytecode). 

