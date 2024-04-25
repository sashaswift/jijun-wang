# Transaction Context

## 场景（Scenario)

- 在商业票据示例中，paper contract最初定义它负责的商业票据列表的名称。随后每笔交易都引用此列表；
  + 随后每笔交易都引用此列表
  + 发行交易向其添加新票据，买入交易更改其所有者，赎回交易将其标记为完成。
  + 在编写智能合约时，初始化和调用顺序交易中的特定变量通常很有帮助
- 智能合约交易上下文允许智能合约在交易调用中定义和维护用户变量



## 编程(Programming)

- 构造智能合约时，开发人员可以选择重写内置的Context类的 `createContext()`方法来创建自定义上下文的Context

  ```javascript
  createContext() {
      new CommercialPaperContext();
  }
  ```

- 在示例中，见证`CommercialPaperContext`是如何通过this方式来自定义上下文（context),如何将特定变量 `PaperList`添加到自身

  ```javascript
  CommercialPaperContext extends Context {
      constructor () {
          this.paperList = new PaperList(this);
      }
  }
  ```

- 当 `createContext()`方法返回时，已经创建一个自定义上下文 `ctx`,其中包含 `paperList`作为其变量之一

- 随后，每当调用智能合约进行交易（如发行、购买或赎回）时，此上下文都会传递给它。

- 发行交易的方法

  ```javascript
  ctx.paperList.addPaper(...);
  ctx.stub.putState(...);
  ```





## 结构（Structure)

- 正如在示例中所看到的，事务上下文可以包含任意数量的用户变量，例如：`paperList`
- 事务上下文还包括两个内置元素，它们提供对各种Fabric功能的访问，从提交事务的客户端应用程序到账本访问
  + `ctx.stub`用于访问API，这些API提供广泛的事务处理操作.
  + `ctx.clientIdentity`用于获取有关提交交易的用户身份的信息



## 存根（Stub）

存根中的API分为以下几类：

- **世界状态数据API**。这些API使智能合约能够使用其密钥从世界状态中获取、防止和删除与单个对象相对应的状态

  + `getState()`
  + `putState()`
  + `deleteState()`

  这些基本API由查询API补充，使合约能够检索一组状态，而不是单个状态。该集要么由一系列键值定义，使用完整键或部分键，要么根据基础世界状态数据库中的值进行查询。对于大型查询，可以对结果集进行分页来减少存储要求：

  + `getStateByRange(
  + `getStateByRangeWithPagination()`
  + `getStateByPartialCompositeKey()`
  + `getStateByPartialCompositeKeyWithPagination()`
  + `getQueryResult()`
  + `getQueryResultWithPagination()`

- **私有数据API**。这些API使智能合约能够与私有数据集合进行交互。它们类似于用于世界状态交互的API，但用于私有数据。有一些API可以通过其密钥获取、放置和删除私有数据状态

  + `getPrivateData()`
  + `putPrivateData()`
  + `deletePrivateData()`

  这组API由一组用于查询私有数据的API补充，这些API允许智能合约根据一系列键值（完整或部分键）或根据底层世界状态数据库中的值进行查询，从私有数据集合中检索一组状态。**目前没有用于私有数据收集的分页API**
  
  + `getPrivateDataByRange()`
  + `getPrivateDataByPartialCompositeKey()`
  + `getPrivateDataQueryResult()`
  
- **事务API**。智能合约使用这些API来检索有关智能合约正在处理的当前交易提案的详细信息。这包括交易标识符和创建交易建议的时间

  + `getTxID()`：返回当前交易提案的标识符
  + `getTxTimestamp()`:返回应用程序创建当前交易提案时的时间戳
  + `getCreator()`:返回交易提案创建者的原始身份（X.509或其他身份）。如果这是X.509证书，则使用 `ctx.ClientIdentity`
  + `getSignedProposal()`:返回智能合约正在处理的当前交易提案的签名副本
  + `getBinding()`:用于防止使用随机数恶意或意外重放事务。（出于实际目的，随机数是由客户端应用程序生成并合并到加密哈希中的随机数）
  + `getTransient()`：允许智能合约访问应用程序传递给智能合约的瞬态数据。瞬态数据是应用程序与智能合约交互的私有数据，不记录在账本上，通常与私人数据收集结合使用

- **密钥API**。智能合约使用密钥API来操作世界状态中的状态密钥和私有数据集合。

  + `createCompositeKey()`

  + `splitCompositeKey()`

  + `setStateValidationParameter()`

  + `getStateValidationParameter()`

  + `getPrivateDataValidationParameter()`

  + `setPrivateDataValidationParameter()`

  + `getHistoryForKey()`

    这些API中最简单的API允许智能合约从其各个组件中形成和拆分复合键。稍微高级一点的是 `ValidationParameter()`API。它获取并设置事件状态和私有数据的基于状态的背书策略。最后 `getHistoryForKey()`通过返回一组存储值（包括执行状态更新的交易标识符）来检索状态的历史记录，从而允许从区块链中读取交易

- **事件API**用于管理智能合约中的事件处理

  + `setEvent()`

- **实用程序API**是一组有用的API,这些API不容易归入预定义的类别，因此将它们组合在一起。包括检索当前通道名称并将控制权传递给同一节点上的不同链码

  + `getChannelID()`                                     
  + `invokeChaincode()`
  + 在任何peer节点上运行的智能合约都可以使用此API相互调用。此API确定应用程序在哪个通道上调用了智能合约
  + `MagnetoCorp`拥有的Peer3上安装了多个智能合约。这些智能合约能够使用此API相互调用。智能合约必须并置；无法在不同的节点上调用智能合约
  + 其中一些实用程序API仅在使用低级链码而不是智能合约时使用。这些API主要用于链码输入的详细操作；智能合约 `Contract`类会自动为开发人员执行这些参数封送处理
  + `getFunctionAndParameters()`
  + `getStringArgs()`
  + `getArgs()`



## 客户身份（ClientIdentity)

- 在大多数情况下，提交事务的应用程序将使用X.509证书。在此示例中，`Isabella`在其应用程序中使用 `CA1`颁发的X.509证书来签署事务 `t6`中的提案
- `ClientIdentity`获取 `getCreator()`返回的信息，并在其上放置一组 X.509实用程序API，以便于此常见用例使用
  + `getX509Certificate()`:返回事务提交者的完整的X.509证书，包括其所有属性及其值。
  + `getAttributeValue()`:返回特定X.509属性的值，例如，组织单位OU或可分辨名称DN参见交互点
  + `assertAttributeValue()`：如果X.509属性的指定属性具有指定值，则返回true
  + `getID()`：根据事务提交者的唯一身份，根据其可分辨名称和办法CA的可分辨名称。格式为 `x509::{subject DN}::{issuser DN}`
  + `getMSPID()`:返回交易提交者的通道MSP。这允许智能合约根据提交者的组织身份做出处理决策
