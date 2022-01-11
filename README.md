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
├── fuzz
├── initial_.sh
├── rename_src.sh
├── run.sh
└── README.md
```

* `sFuzz`: The main fuzzing module of TAFuzzer
* `bran`: The abstract interpreter for path analysis
* `tools`: Other static analysis tools for extracting vulnerability-specific patterns
  * `requirements.txt`：Python dependencies
* `assets`:
  * `ReentrancyAttacker_model.sol`: The template for an attacker contract
  * `ReentrancyAttacker.sol`: The attacker contract generated based on the template
* `source_codes`: Restore the source code of the contract under test
* `contracts/example1`: Restore the compiled results of the contract under test
* `branch_msg`: Restore the intermediate representations of the contract under test
* `logs`: Restore the execution report during fuzzing
* `fuzz`: Execute the fuzzer

## Quick Start

- Initialization and Install system dependencies

```bash
./initial_.sh
```

- Make workspace for the contract in directory `source_codes`

```bash
./rename_src.sh
```

- Run TAFuzzer and perform vulnerability detection

```bash
./run.sh
```

- The code is adapted from [sFuzz](https://github.com/duytai/sFuzz) (a state-of-the-art fuzzer for smart contracts) and [bran](https://github.com/Practical-Formal-Methods/bran) (a static analysis framework for EVM bytecode). 

