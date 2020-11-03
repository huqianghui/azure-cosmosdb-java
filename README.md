# cosmosDB

## cosmosDB的几个主要特征：

1）	都是现实文档数据库 document DB，存储的是json内容。对标的是mongoDB

2）	Cosmos本义是星球的意思，所以它可以在不同地理位置实现同步策略

3）	CosmosDB满足五个不同层级的事务，从strong 到eventual，一致性和可用性的权衡

4）	是一个nosql，支持不同的API，sql，mongoDB，列数据库，图数据库等API

5）可以自动建立所有列的索引和RowId，一些管理字段，这个和es有点类似

## cosmos的性能单位 RU（request unit）的说明

Azure Cosmos DB 中的请求单位：

Azure Cosmos DB 支持多种 API，例如 SQL、MongoDB、Cassandra、Gremlin 和表。 每个 API 具有自身的数据库操作集。 这些操作包括简单的点读取和写入，以及复杂的查询等等。 每个数据库操作根据其复杂性消耗系统资源。所有数据库操作的成本将由 Azure Cosmos DB 规范化，并以“请求单位”（缩写为 RU）表示。 你可以将 RU 视为性能货币，它抽象化了执行 Azure Cosmos DB 支持的数据库操作所需的系统资源，例如 CPU、IOPS 和内存。对于一个 1 KB 的项，执行点读取（即，按 ID 和分区键值提取单个项）的成本是 1 个请求单位（或 1 RU）。 以类似方式为其他所有数据库操作分配 RU 成本。 不管使用哪个 API 来与 Azure Cosmos 容器和数据库操作交互，都始终以 RU 来计量成本。 无论数据库操作是写入、点读取还是查询，都始终以 RU 来计量成本。

## CosmosDB的NoSql本质

Merge on Read （not copy on write）
CosmosDB在写时候，不做任何校验，而是在读取数据的时候根据不同的API 类型来做merge

## CosmosDB的资源概念说明

Azure Cosmos 数据库:

可以在帐户下创建一个或多个 Azure Cosmos 数据库。 数据库类似于命名空间， 数据库是一组 Azure Cosmos 容器的管理单元

Azure Cosmos 容器:

是预配的吞吐量和存储的缩放单元。 容器会进行水平分区，然后在多个区域间复制。 添加到容器的项将自动划分为逻辑分区，这些分区基于分区键分布在物理分区中。 容器上的吞吐量均匀分布在物理分区中。 
Azure Cosmos 容器是与架构无关的项容器。 容器中的项可以采用任意架构。 例如，可以在同一个容器中放置一个表示人员的项，以及一个表示汽车的项。 默认情况下，添加到容器的所有项会自动编制索引，不需要进行显式的索引或架构管理。 通过在容器上配置的索引策略，可以自定义索引行为。
以及一些其他的设置。可以在 Azure Cosmos 容器上指定一个唯一键约束。 通过创建唯一键策略，可确保每个逻辑分区键的一个或多个值的唯一性。 如果使用唯一键策略创建容器，则无法创建值与唯一键约束指定的值重复的任何新项或更新的项。 若要了解详细信息，请参阅唯一键约束。

Azure Cosmos 项：

根据所用的 API，Azure Cosmos 项可以代表集合中的文档、表中的行，或者图形中的节点或边缘。

## cosmosDB 是无schema的，而且partition column和Id都不是必须的


********************************************** original project  information **********************************************************

# Project Name

Azure Spring Data Cosmos getting started tutorial.

## Features

This tutorial provides getting started features for `azure-spring-data-cosmos` Java SQL API modules.

## Getting Started

### Prerequisites

- `Java Development Kit 8` or `JDK 11` if you run the `azure-spring-data-cosmos-java-11-getting-started`. 
- An active Azure account. If you don't have one, you can sign up for a [free account](https://azure.microsoft.com/free/). Alternatively, you can use the [Azure Cosmos DB Emulator](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator) for development and testing. As emulator https certificate is self signed, you need to import its certificate to java trusted cert store, [explained here](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator-export-ssl-certificates)
- (Optional) SLF4J is a logging facade.
- (Optional) [SLF4J binding](http://www.slf4j.org/manual.html) is used to associate a specific logging framework with SLF4J.
- (Optional) Maven.

SLF4J is only needed if you plan to use logging, please also download an SLF4J binding which will link the SLF4J API with the logging implementation of your choice. See the [SLF4J user manual](http://www.slf4j.org/manual.html) for more information.

### Installation

mvn clean install

### Quickstart

1. git clone https://github.com/Azure-Samples/azure-spring-data-cosmos-java-sql-api-getting-started.git
2. cd azure-spring-data-cosmos-java-sql-api-getting-started
3. cd azure-spring-data-cosmos-java-getting-started (for Java8) or azure-spring-data-cosmos-java-11-getting-started (for Java11)
4. mvn spring-boot:run

## Resources

Please refer to azure spring data cosmos java sql api [source code](https://github.com/Azure/azure-sdk-for-java/tree/master/sdk/cosmos) for more information.
