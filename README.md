 # Apoolminer for Quai

```powershell
 $$$$$$\  $$$$$$$\   $$$$$$\   $$$$$$\  $$\       
$$  __$$\ $$  __$$\ $$  __$$\ $$  __$$\ $$ |      
$$ /  $$ |$$ |  $$ |$$ /  $$ |$$ /  $$ |$$ |      
$$$$$$$$ |$$$$$$$  |$$ |  $$ |$$ |  $$ |$$ |      
$$  __$$ |$$  ____/ $$ |  $$ |$$ |  $$ |$$ |      
$$ |  $$ |$$ |      $$ |  $$ |$$ |  $$ |$$ |      
$$ |  $$ |$$ |       $$$$$$  | $$$$$$  |$$$$$$$$\ 
\__|  \__|\__|       \______/  \______/ \________|
```

## Introduction

The best Optimization Miner for Quai.

## Disclaimer

[apool.io](https://www.apool.io/) & [apoolminer_github](https://github.com/apool-io/quaiminer) are the only 2 officially maintained site for publishing information and new releases of apoolminer.

## Install

Always get the lastest version from the [releases](https://github.com/apool-io/quaiminer/releases)

and then extract the file


## Usage

Please refer to the usage help (`./apoolminer --help`):

If you didn't have an apool account, Head over to [Apool Website](https://www.apool.io) to finish email registration, and Copy the sub-account from [myminer page](https://www.apool.io/myMiner).

Then start miner like:

```powershell
./apoolminer --algo quai --account <your sub-account> --pool <quai proxy> [OPTIONS] 
```

```powershell
Options:
  -A, --algo <ALGORITHM>               Specify algorithm, support qubic,aleo,ore,qubic_ore,quai,qubic_quai,qubic_xmr [default: qubic]
      --account <ACCOUNT>              Specify the main account
      --account-slave <ACCOUNT_SLAVE>  Specify the slave account, use main account if not set
      --worker <WORKER>                Specify the worker name. Note: The name consists of numbers and letters and cannot exceed 15 characters in length
      --pool <POOL>                    Specify the main pool server address
      --pool-slave <POOL_SLAVE>        Specify the slave pool server address
  -g, --gpu <GPU>                      Specify the index of GPU. Specify multiple times to use multiple GPUs, example: -g 0 -g 1 -g 2
  -p, --parallel <PARALLEL>            Specify the number of parallel jobs per GPU [default: 0]
      --cpu-off                        Close main CPU mining
      --cpu-off-slave                  Close slave CPU mining
  -o, --log <LOG>                      Specify the log file
      --local-time                     Use the local time for log message timestamps
      --vf                             More information about version
      --rest                           Enable REST server
      --port <PORT>                    Specify the port for the REST server [default: 5001]
  -h, --help                           Print help
  -V, --version                        Print version

```
  
## GPU supports

- NVIDIA Turing GPU (RTX20)
- NVIDIA Ampere GPU (RTX30)
- NVIDIA Ada Lovelace GPU (RTX40)

## API Reference

### miner status 

**Path：** /status

**Method：** GET

**Response:**

```
{
  "code": 200,
  "data": {
    "online": false
  }
}
```

### miner info 

The /gpu API will return all devices, including cpu.

**Path：** /gpu

**Method：** GET

**Response:**  

```
{
"code": 200,
"data": {
    "gpus": [{
        "cclk": 1635, //graphics clock
        "ctmp": 74, // gpu temperature
        "device": "2060SU", //gpu device 
        "fan": 76, //fan
        "gmclk": 6801, //graphics memory clock
        "id": 0,
        "inval": 0, //invalid
        "mtmp": "89", //max temperature
        "power": 169, //power
        "proof": 0.0, //proof rate
        "statle": 0, // statle
        "valid": 0 // valid
    }],
    "uptime": 197 //program up time 
}
```

**Usage:**

```powershell
./apoolminer --algo quai --account <your sub-account> --rest --port 5001 --pool <coin proxy> [OPTIONS]    
```

## Changelog

### 2.8.3
GPU: Add quai algorithm, support qubic+quai idle mining.
