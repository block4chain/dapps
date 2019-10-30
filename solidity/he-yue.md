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
      <td style="text-align:left">Data Location</td>
      <td style="text-align:left"><code>memory</code>, <code>storage</code>, <code>calldata</code>
      </td>
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
      <td style="text-align:left">mapping</td>
      <td style="text-align:left"><code>mapping(_KeyType =&gt; _ValueType)</code>
      </td>
      <td style="text-align:left"></td>
    </tr>
  </tbody>
</table>

