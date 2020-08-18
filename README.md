catapult-opt-in-toolkit
================

Tool to pull optin transactions from nis1 networks and create symbol nemesis transactions.

[![oclif](https://img.shields.io/badge/cli-oclif-brightgreen.svg)](https://oclif.io)
[![Version](https://img.shields.io/npm/v/catapult-opt-in-toolkit.svg)](https://npmjs.org/package/catapult-opt-in-toolkit)
[![Downloads/week](https://img.shields.io/npm/dw/catapult-opt-in-toolkit.svg)](https://npmjs.org/package/catapult-opt-in-toolkit)
[![License](https://img.shields.io/npm/l/catapult-opt-in-toolkit.svg)](https://github.com/nemgrouplimited/catapult-opt-in-toolkit/blob/master/package.json)

<!-- toc -->
* [Installation](#installation)
* [E2E Test](#e2e-test)
* [Usage](#usage)
* [Commands](#commands)
<!-- tocstop -->

# Installation
```sh-session
npm install
npm pack
npm install -g
```

# E2E Test

1. Pulls transactions from nis1.
2. Generates the opt-in preset yml. 
3. Runs the Network using [symbol-bootstrap](https://github.com/fboucquez/symbol-bootstrap).

```sh-session
npm run e2e
```

Once the network running, you can test the populated transactions and accounts via:

* http://localhost:3000/transactions/confirmed?height=1&pageSize=100
* http://localhost:3000/accounts
* http://localhost:3000/node/info


# Usage
<!-- usage -->
```sh-session
$ npm install -g catapult-opt-in-toolkit
$ catapult-opt-in-toolkit COMMAND
running command...
$ catapult-opt-in-toolkit (-v|--version|version)
catapult-opt-in-toolkit/0.0.0 linux-x64 node-v12.16.3
$ catapult-opt-in-toolkit --help [COMMAND]
USAGE
  $ catapult-opt-in-toolkit COMMAND
...
```
<!-- usagestop -->

Alternative, if you don't have the tool globally installed, you can run
```
./bin/run COMMAND
```
Example:
```
./bin/run generate --overrideFiles
```

# Commands
<!-- commands -->
* [`catapult-opt-in-toolkit generate`](#catapult-opt-in-toolkit-generate)
* [`catapult-opt-in-toolkit help [COMMAND]`](#catapult-opt-in-toolkit-help-command)
* [`catapult-opt-in-toolkit read`](#catapult-opt-in-toolkit-read)
* [`catapult-opt-in-toolkit subscribe`](#catapult-opt-in-toolkit-subscribe)

## `catapult-opt-in-toolkit generate`

generate test data

```
USAGE
  $ catapult-opt-in-toolkit generate

OPTIONS
  -h, --help                                                     show CLI help
  -n, --catapultNetworkType=104|152|96|144                       [default: 152] The catapult network type.

  -o, --outputFolder=outputFolder                                [default: output] Target folder where files are
                                                                 generated.

  -r, --overrideFiles                                            Override the files in output

  --catapultGenerationHash=catapultGenerationHash                [default:
                                                                 7391E2EF993C70D2F52691A54411DA3BD1F77CF6D47B8C8D8832C89
                                                                 0069AAAAA] The catapult generation hash.

  --command=nemesisFiles|bootstrapPreset|propertyFiles|csvFiles  [default: propertyFiles] The types of files to be
                                                                 generated.

  --generateBalances=generateBalances                            [default: 100] Number of balances to be generated

  --generateMultisigns=generateMultisigns                        [default: 100] Number of multisig transactions to be
                                                                 generated

  --generateNamespaces=generateNamespaces                        [default: 100] Number of namespace transactions to be
                                                                 generated

  --generateVrfs=generateVrfs                                    [default: 100] Number of VRF transactions to be
                                                                 generated

EXAMPLE
  $ catapult-opt-in-toolkit generate --command propertyFiles
```

_See code: [src/commands/generate.ts](https://github.com/nemgrouplimited/catapult-opt-in-toolkit/blob/v0.0.0/src/commands/generate.ts)_

## `catapult-opt-in-toolkit help [COMMAND]`

display help for catapult-opt-in-toolkit

```
USAGE
  $ catapult-opt-in-toolkit help [COMMAND]

ARGUMENTS
  COMMAND  command to show help for

OPTIONS
  --all  see all commands in CLI
```

_See code: [@oclif/plugin-help](https://github.com/oclif/plugin-help/blob/v3.1.0/src/commands/help.ts)_

## `catapult-opt-in-toolkit read`

read data from nis 1 network

```
USAGE
  $ catapult-opt-in-toolkit read

OPTIONS
  -h, --help                                                                                  show CLI help

  -n, --catapultNetworkType=104|152|96|144                                                    [default: 152] The
                                                                                              catapult network type.

  -o, --outputFolder=outputFolder                                                             [default: output] Target
                                                                                              folder where files are
                                                                                              generated.

  -r, --overrideFiles                                                                         Override the files in
                                                                                              output

  --brokerAddress=brokerAddress                                                               [default:
                                                                                              amqp://localhost] The
                                                                                              broker address.

  --catapultGenerationHash=catapultGenerationHash                                             [default:
                                                                                              7391E2EF993C70D2F52691A544
                                                                                              11DA3BD1F77CF6D47B8C8D8832
                                                                                              C890069AAAAA] The catapult
                                                                                              generation hash.

  --catapultUrl=catapultUrl                                                                   [default:
                                                                                              http://localhost:3001] The
                                                                                              catapult url.

  --command=readToBroker|readToCsv|readToProperties|readToNemesisFiles|readToBootstrapPreset  [default:
                                                                                              readToProperties] Where to
                                                                                              delegate the results.

  --nisNetworkId=nisNetworkId                                                                 [default: -104] The nis
                                                                                              one network id

  --nisOptInAddress=nisOptInAddress                                                           [default:
                                                                                              TAHVSTHAAVKZLFFYKZSENAZJMG
                                                                                              TOMRRAXTW3YNHF] The nis 1
                                                                                              opt in address.

  --nisUrl=nisUrl                                                                             [default:
                                                                                              http://hugetestalice2.nem.
                                                                                              ninja:7890] The nis 1 url.

  --readPageSize=readPageSize                                                                 [default: 20] The read
                                                                                              page size

  --snapshotHeight=snapshotHeight                                                             [default: -1] The nis 1
                                                                                              snapshot height, -1 means
                                                                                              the latest height

EXAMPLE
  $ catapult-opt-in-toolkit read --command readToProperties
```

_See code: [src/commands/read.ts](https://github.com/nemgrouplimited/catapult-opt-in-toolkit/blob/v0.0.0/src/commands/read.ts)_

## `catapult-opt-in-toolkit subscribe`

read data from nis 1 network

```
USAGE
  $ catapult-opt-in-toolkit subscribe

OPTIONS
  -h, --help
      show CLI help

  -n, --catapultNetworkType=104|152|96|144
      [default: 152] The catapult network type.

  -o, --outputFolder=outputFolder
      [default: output] Target folder where files are generated.

  -r, --overrideFiles
      Override the files in output

  --brokerAddress=brokerAddress
      [default: amqp://localhost] The broker address.

  --catapultGenerationHash=catapultGenerationHash
      [default: 7391E2EF993C70D2F52691A54411DA3BD1F77CF6D47B8C8D8832C890069AAAAA] The catapult generation hash.

  --catapultUrl=catapultUrl
      [default: http://localhost:3001] The catapult url.

  --command=subscriberToCsv|subscriberToProperties|subscriberToNemesisFiles|subscriberBootstrapPreset
      [default: subscriberToProperties] Where to delegate the results.

  --nisNetworkId=nisNetworkId
      [default: -104] The nis one network id

  --nisOptInAddress=nisOptInAddress
      [default: TAHVSTHAAVKZLFFYKZSENAZJMGTOMRRAXTW3YNHF] The nis 1 opt in address.

  --nisUrl=nisUrl
      [default: http://hugetestalice2.nem.ninja:7890] The nis 1 url.

  --readPageSize=readPageSize
      [default: 20] The read page size

  --snapshotHeight=snapshotHeight
      [default: -1] The nis 1 snapshot height, -1 means the latest height

EXAMPLE
  $ catapult-opt-in-toolkit read --command subscriberToProperties
```

_See code: [src/commands/subscribe.ts](https://github.com/nemgrouplimited/catapult-opt-in-toolkit/blob/v0.0.0/src/commands/subscribe.ts)_
<!-- commandsstop -->
