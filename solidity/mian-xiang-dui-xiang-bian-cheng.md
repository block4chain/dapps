---
description: Solidity合约支持继承，一种类型面向对象的编程方法
---

# 合约继承

## 继承

* 合约支持多重继承，并且支持多态
* 所有的合约方法都是虚函数
* 如果合约继承多个合约，部署到区块链时只有一个合约，并且调用父合约方法时是一个内部调用，而不是一个消息

关键字`is`用于合约继承

```text
contract Owned {
    constructor() public { owner = msg.sender; }
    address payable owner;
}

contract Mortal is Owned {
    function kill() public {
        if (msg.sender == owner) selfdestruct(owner);
    }
}
```

### 多重继承

```text
contract Named is Owned, Mortal {
    constructor(bytes32 name) public {
        Config config = Config(0xD5f9D8D94886E70b06E474c3fB14Fd43E2f23970);
        NameReg(config.lookup(1)).register(name);
    }
    function kill() public {
        if (msg.sender == owner) {
            Config config = Config(0xD5f9D8D94886E70b06E474c3fB14Fd43E2f23970);
            NameReg(config.lookup(1)).unregister();
            Mortal.kill();  //调用父方法
        }
    }
}
```

## 抽象合约

如果合约存在至少一个没有实现的方法，则该合约是一个抽象合约

```text
contract Feline {
    function utterance() public returns (bytes32);
}
```

## 接口

```text
pragma solidity >=0.5.0 <0.7.0;
interface Token {
    enum TokenType { Fungible, NonFungible }
    struct Coin { string obverse; string reverse; }
    function transfer(address recipient, uint amount) external;
}
```

* 接口不可继承其它接口或合约
* 接口中的所有方法必须是external
* 接口不可以定义构造函数
* 接口不可以定义状态变量

