# Introduction

- **Protocol name**: Pendle
- **Category**: DeFi
- **Smart Contract**: Address.sol

## Function Analysis

## Code snapshot
[Download Code](path/to/code/file.zip)

- **Used call method**: call
- **Function Name**: sendValue
- **Block explorer link**: [Etherscan - Address.sol](https://etherscan.io/token/0x808507121b80c02388fad14726482e061b8da827#code)

## Purpose

The `sendValue` function is a safer alternative to Solidity's native transfer function. It sends a specified amount of wei to a recipient, forwarding all available gas and reverting on errors.

## Detailed usage

The `sendValue` function uses the low-level `call` method with an empty data payload to transfer `amount` wei to the recipient. This method is chosen over `transfer` to avoid the gas limit issues introduced by EIP-1884, which can make contracts unable to receive funds due to the 2300 gas limit imposed by `transfer`. The `call` method forwards all available gas to the recipient, ensuring that the transfer succeeds even if the recipient requires more than 2300 gas to complete its operations. The function first checks if the calling contract has sufficient balance to send the specified amount. If the call fails, the function reverts with an error message.

## Impact

The `sendValue` function contributes significantly to the robustness and reliability of the Address utility library. By ensuring that transfers of ETH are less likely to fail due to gas limits, it improves the overall usability and safety of smart contracts using this library. This function is essential for scenarios where contracts need to send ETH to other contracts or externally owned accounts (EOAs) without encountering unexpected failures due to gas restrictions.
