---
description: 合约类似于面向对象中的类，一个sodility源文件中可以包含任意多个合约定义。
---

# 合约

## 定义

关键字`contract`用来定义一个合约

```cpp
pragma solidity >=0.4.0 <0.7.0;
contract SimpleStorage {
    //定义合约要素....
}
```

## 状态变量

合约可以创建状态变量用来持久化存储数据。

```text
contract SimpleStorage {
    uint storedData; // 状态变量
}
```

### 值类型

<table>
  <thead>
    <tr>
      <th style="text-align:left">&#x7C7B;&#x578B;</th>
      <th style="text-align:left">&#x5173;&#x952E;&#x5B57;</th>
      <th style="text-align:left">&#x542B;&#x4E49;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">&#x5E03;&#x5C14;&#x7C7B;&#x578B;</td>
      <td style="text-align:left"><code>bool</code>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">&#x6574;&#x578B;</td>
      <td style="text-align:left">
        <p><code>uint8</code>, <code>uint16</code>, <code>uint24</code>, ... <code>uint256</code>(<code>uint</code>)</p>
        <p><code>int8</code>, <code>int16</code>, <code>int24</code>, ..., <code>int256</code>(<code>int</code>)</p>
      </td>
      <td style="text-align:left">uint&#x9ED8;&#x8BA4;&#x662F;uint256, int&#x9ED8;&#x8BA4;&#x662F;int256</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x5B9A;&#x70B9;&#x5C0F;&#x6570;</td>
      <td style="text-align:left"><code>ufixedMxN</code>,<code>fixedMxN</code>
      </td>
      <td style="text-align:left">M&#x4EE3;&#x8868;&#x6574;&#x6570;&#x4F4D;, N&#x4EE3;&#x8868;&#x5C0F;&#x6570;&#x4F4D;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x5730;&#x5740;</td>
      <td style="text-align:left"><code>address</code>, <code>address payable</code>
      </td>
      <td style="text-align:left">
        <p>&#x4EE3;&#x8868;&#x4E00;&#x4E2A;&#x6709;&#x6548;&#x7684;&#x4EE5;&#x592A;&#x574A;&#x5730;&#x5740;.</p>
        <p><code>address payable</code>&#x5305;&#x542B;<code>transfer</code>&#x548C;<code>send</code>&#x65B9;&#x6CD5;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#x5408;&#x7EA6;</td>
      <td style="text-align:left"><code>contract</code>
      </td>
      <td style="text-align:left">&#x5408;&#x7EA6;&#x672C;&#x8EAB;&#x4E5F;&#x662F;&#x4E00;&#x79CD;&#x7C7B;&#x578B;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x5B9A;&#x957F;&#x5B57;&#x8282;&#x6570;&#x7EC4;</td>
      <td style="text-align:left"><code>bytes1</code>,<code>bytes2</code>,<code>bytes3</code>,...,<code>bytes32</code>
      </td>
      <td style="text-align:left">bytes&#x9ED8;&#x8BA4;&#x662F;bytes32</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x53D8;&#x957F;&#x5B57;&#x8282;&#x6570;&#x7EC4;</td>
      <td style="text-align:left"><code>bytes</code>, <code>string</code>
      </td>
      <td style="text-align:left">&#x4E0D;&#x53EF;&#x4EE5;&#x58F0;&#x660E;&#x4E3A;&#x503C;&#x7C7B;&#x578B;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x679A;&#x4E3E;</td>
      <td style="text-align:left"><code>enum</code>
      </td>
      <td style="text-align:left">&#x81EA;&#x5B9A;&#x4E49;&#x679A;&#x4E3E;&#x7C7B;&#x578B;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#x51FD;&#x6570;</td>
      <td style="text-align:left">&#x51FD;&#x6570;&#x7B7E;&#x540D;</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">Array</td>
      <td style="text-align:left"><code>T[k]</code>, <code>T[]</code>
      </td>
      <td style="text-align:left">
        <p><code>T[k]</code>&#x58F0;&#x660E;&#x4E00;&#x4E2A;&#x5B9A;&#x957F;&#x6570;&#x7EC4;</p>
        <p><code>T[]</code>&#x58F0;&#x660E;&#x4E00;&#x4E2A;&#x53D8;&#x957F;&#x6570;&#x7EC4;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Struct</td>
      <td style="text-align:left"><code>struct</code>
      </td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">Map</td>
      <td style="text-align:left"><code>mapping(_KeyType =&gt; _ValueType)</code>
      </td>
      <td style="text-align:left"></td>
    </tr>
  </tbody>
</table>### 数据位置

引用类型: Array、Struct、Map有需要通过标注\(annotation\)声明数据存储的位置:

* memory

数据没有存储在合约的状态数据库中

* storage

数据存储在合约的状态数据库中

* calldata

类型memory，但不可修改

```text
uint[] storage y = x;
struct memory z = x;
```

Map类型数据只能用`storage`标注

### 可见修饰符

状态变量可以用一些修饰符修饰，声明变量的可见性:

| 修饰符 | 含义 |
| :--- | :--- |
| public | 自动生成一个getter方法 |
| internal | 只能被当前合约或子合约访问 |
| private | 只能被当前合约访问 |

## 函数

关键字`function`合约可以声明若干函数

```text
function <函数名>(<parameter types>) {internal|external|public|private} [pure|view|payable] [returns (<return types>)]
```

### 可见性

通过修饰符可以声明函数的可见性:

| 修饰符 | 含义 |
| :--- | :--- |
| external | 函数可以被外部合约或交易调用 |
| public | 可以被消息、合约方法、子合约方法调用 |
| internal | 合约方法、子合约方法调用 |
| private | 本合约方法调用 |

### 函数重载

合约函数支持重载，重载函数通过函数参数区分。

### 只读函数

关键字`view`可以声明函数不会直接修改状态变量 

### 纯函数

关键字`pure`可以声明函数不会直接读取或修改状态变量

### 降级函数

合约可以定义一个且只能定义一个匿名函数，该函数没有参数，也没有返回值，并且被必须被external修饰，这个函数称为降级函数。

降级函数在外部调用没有匹配合约方法时被调用。

### 可支付方法

关键字`payable`将方法声明为可支付方法。即可以向该方法发送以太币。

```text
pragma solidity ^0.4.4;
contract  Sample {
    uint amount =0;
    function payme() payable{
        amount += msg.value;
    }
}
```

给合约定义一个payable的降级方法可以将合约声明为可支付合约，即可以向该合约转帐。

## 函数修改器

合约支持定义若干函数修改器，从而改变函数执行的效果

```text
//定义函数修改器
contract owned {
    modifier onlyOwner {
        require(
            msg.sender == owner,
            "Only owner can call this function."
        );
        _;  //被修饰函数执行到此位置
    }
}
//使用, mortal继承owned
contract mortal is owned {
    function close() public onlyOwner {
        selfdestruct(owner);
    }
}
```

## 事件

* 事件\(Event\)允许合约向外部发出消息，客户端可以监听该消息。
* 事件不可继承

```text
pragma solidity >=0.4.21 <0.7.0;
contract ClientReceipt {
    event Deposit(
        address indexed _from,
        bytes32 indexed _id,
        uint _value
    );
    function deposit(bytes32 _id) public payable {
        emit Deposit(msg.sender, _id, msg.value);
    }
}
```







