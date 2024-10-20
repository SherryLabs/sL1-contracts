# SL1 Smart Contracts - Avalanche Summit Hackathon

## SL1Sender.sol

Este contrato se utiliza para enviar cualquier mensaje a cualquier L1. Permite ejecutar cualquier función en cualquiera de estas L1s.

### Main Function - `sendMessage`

```solidity
    function sendMessage(
        address _destinationContract,
        bytes calldata _encodedFunctionCall,
        address _destinationAdress,
        bytes32 _destinationChain,
        uint256 _gasLimit
    ) public {}
```

#### Descripción de la función

La función `sendMessage` permite enviar un mensaje codificado a través de un protocolo cross-chain para ejecutar una función específica en un contrato de destino en otra blockchain.

#### Parámetros

- `address _destinationContract`: La dirección del contrato en la blockchain de destino donde se ejecutará la función.
- `bytes calldata _encodedFunctionCall`: La llamada de función codificada que incluye la firma de la función y los parámetros. Esta llamada debe estar codificada utilizando abi.encodeWithSignature o abi.encodePacked.
- `address _destinationAddress`: La dirección del contrato en la blockchain de destino que recibirá el mensaje.
- `bytes32 _destinationChain`: El identificador de la blockchain de destino. Este identificador es específico del protocolo cross-chain que se esté utilizando.
- `uint256 _gasLimit`: El límite de gas que se asignará para la ejecución de la función en la blockchain de destino. Este valor debe ser suficiente para cubrir el costo de la ejecución de la función.

#### Ejemplo de Uso

```solidity
address destinationContract = 0x1234567890abcdef1234567890abcdef12345678;
bytes memory encodedFunctionCall = abi.encodeWithSignature("someFunction(uint256,address)", 42, 0xabcdefabcdefabcdefabcdefabcdefabcdef);
address destinationAddress = 0xabcdefabcdefabcdefabcdefabcdefabcdefabcdef;
bytes32 destinationChain = 0xabcdefabcdefabcdefabcdefabcdefabcdefabcdefabcdefabcdefabcdefabcdef;
uint256 gasLimit = 200000;

SL1Sender.sendMessage(destinationContract, encodedFunctionCall, destinationAddress, destinationChain, gasLimit);
```

En este ejemplo, se envía un mensaje para ejecutar la función `someFunction` en el contrato de destino con los parámetros `42` y `0xabcdefabcdefabcdefabcdefabcdefabcdef`. El mensaje se envía a la dirección del contrato de destino especificada por `destinationAddress` en la blockchain de destino especificada por `destinationChain` con un límite de gas de `200000`.

Este enfoque permite una comunicación flexible y dinámica entre contratos en diferentes blockchains, facilitando la interoperabilidad cross-chain.


## Contract Addresses

| Contract Name | Address                                      | Chain  |
|---------------|----------------------------------------------|--------|
| `SL1Sender`     | 0x76ceB8017741c7fEAcae7D1179b0d3eB4151dcc4   | `sL1`    |
| `SL1Sender`     | 0x4f34C7119c1C918c606792D8a481D915D845DD2E   | `Dispatch L1`    |
| `SL1Sender`     | 0x7204bdd163A7ACBc6125Bab0a4EA87ebb168ea12   | `Fuji`    |
| `SL1AnyChainReceiver`     | 0x6329dDC217c67718F850657dF9E50025aC0c8dba   | `Dispatch L1`    |
| `SL1AnyChainReceiver`     |    | `Fuji`    |

Examples

| Contract Name | Address                                      | Chain  |
|---------------|----------------------------------------------|--------|
| `Greeting`     | 0x2f4462dab28A090B4BEF9906CCd6bBd803D3E21c   | `Dispatch L1`    |
| `Greeting`     | 0x043135e9dF9f74B9C4580273C418B44fA8896726   | `Fuji`    |


## Chains Data

| L1 Name | ID | type |
|---------|----|------|
|Dispatch | 0xdb76a6c20fd0af4851417c79c479ebb1e91b3d4e7e57116036d203e3692a0856| hex






