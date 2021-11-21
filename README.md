# achi-vanitygen
Achi Vanitygen program is designed to help you easily create Achi vanity addresses with a given pattern. You can use a vanity address program to create a more personalized address. For example, you can create an address that starts with ‘ach1stake’ and ask people to send Achi to ach1stakelhnltrea985k9rhv092wzlje4sp6hvc4gza8u0zlnhqac7qakfzw5 or otherwise use is as any generic Achi address. The amount of time required to find a given pattern depends on how long the pattern is, the speed of the computer(s) employed to do the calculations and luck. On average it takes 8-12 hours to generate vanity address with special 5 symbols after ach1, the more symbols after ach1 in the pattern the more time it takes to generate.

## How it works

Achi Vanitygen gets tasks from Achi Vanitygen Server to start vanity addresses bruteforcing. 

GET /api/v1/get_tasks

Response:

```json
[
  {
    "Seed": "76a2237b76d52e5bf8d72a7584ec33356256a76d87c05aab3895723d98a25df748336374843aae233a42a62b18f56443a7116853422de54ce5fa915fdd1e7990",
    "Prefixes": [
      {
        "Prefix": "sell",
        "Amount": 1
      },
      {
        "Prefix": "stake",
        "Amount": 10
      },
      {
        "Prefix": "l0rd",
        "Amount": 1
      }
    ],
    "StartIndex": 0,
    "EndIndex": 1000,
    "Id": "e9972a6a-9719-4ee0-9b0a-fec3ae68ec1a"
  }
]
```
Found addresses are sent to Achi Vanitygen Server. 

POST /api/v1/task_reports

Payload:

```json
[
  {
    "TaskId": "e9972a6a-9719-4ee0-9b0a-fec3ae68ec1a",
    "Items": [
      {
        "Prefix": "l0rd",
        "MaxAddresses": 1,
        "Addresses": [],
        "PartsAmount": [
          31,
          1,
          0,
          0
        ]
      },
      {
        "Prefix": "sell",
        "MaxAddresses": 1,
        "Addresses": [],
        "PartsAmount": [
          38,
          0,
          0,
          0
        ]
      },
      {
        "Prefix": "stake",
        "MaxAddresses": 10,
        "Addresses": [],
        "PartsAmount": [
          38,
          1,
          0,
          0,
          0
        ]
      }
    ],
    "LastIndex": 1000
  },
]
```


## Usage

You can run Achi Vanitygen either on one PC or on multiple PCs. The connection between server and client parts protected by ssl. To speed-up the process of searching vanity addresses you can run Achi Vanitygen Server and Achi Vanitygen on different PCs. E.g. Server part is run on your PC and Achi Vanitygen is run on one or more remote servers.

``` 
Usage of achi_vanitygen:
  -batch int
    	a batch limit (default 10)
  -port uint
    	an aggregator port (default 18070)
  -server string
    	an aggregator host (default "localhost") 
```

## Quick start

### Step 1 - Download Achi Vanitygen
https://github.com/Achi-Coin/achi-vanitygen

### Step 2 - Start Server

Start server as it is described here https://github.com/Achi-Coin/achi-vanitygen-server/README.md

### Step 3 - Edit start_clients.sh

Replace '127.0.0.1' to IP address of your server or do not make any changes if you run client and server on the same PC

### Step 4 - Start Achi Vanitygen

Run $ watch ./start_clients.sh

