# Online Analytical Processing (OLAP) data stores

[About]()  
[What are your options when choosing an OLAP data store?](#options)  
[How do you choose?](#howtochoose)  
[Key Selection Criteria](#criteria)  
[Capability Matrix](#matrix)   
[Where to go from here](#wheretogo)  

<a name="about"></a>

## <a name="options"></a> What are your options when choosing an OLAP data store?
In Azure, all of the following data stores will meet the core requirements for OLAP:

- [Azure Analysis Services (AAS)](https://docs.microsoft.com/azure/analysis-services/analysis-services-overview)
- [SQL Server Analysis Services (SSAS)](https://docs.microsoft.com/sql/analysis-services/analysis-services)
- [SQL Server with nonclustered columnstore indexes](https://docs.microsoft.com/sql/relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics)

SQL Server Analysis Services (SSAS) offers online analytical processing (OLAP) and data mining functionality for business intelligence applications. You can either install SSAS on local servers, or host within a VM in Azure. Azure Analysis Services (AAS) is a fully managed platform as a service (PaaS) offering that provides the same major features as SSAS, in the cloud. Because AAS lives in the cloud, its servers support connecting to [various data sources](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource) in the cloud and on-premises in your organization.

Beginning with SQL Server 2016 (including Azure SQL Database), you can take advantage of Hybrid Transactional/Analytics Processing (HTAP) through the use of updateable nonclustered columnstore indexes. HTAP enables you to perform OLTP and OLAP processing on the same platform, removing the need to store multiple copies of your data, and eliminating the need for distinct OLTP and OLAP systems. For more information, see [Get started with Columnstore for real time operational analytics](https://docs.microsoft.com/sql/relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics).

## <a name="howtochoose"></a> How do you choose?
Each data store brings with it a unique set of capabilities, giving you options in selecting the one that most closely meets your requirements. 

## <a name="criteria"></a> Key Selection Criteria

The following tables summarize the key differences in capabilities between each. For OLAP scenarios, choose the appropriate system for your needs by answering these questions:

- Do you want a managed service or do you prefer to manage your own physical or virtual servers?
    - If yes, then narrow your options to those that are managed services.
- Do you require secure authentication using Azure Active Directory?
    - If yes, then you will need one of the options that AAD integration.
- Do you want to conduct real-time analytics?
    - If so, narrow your options to those that support real-time analytics. Real-time operational analytics targets the scenario of a single data source such as an enterprise resource planning (ERP) application on which you can run both the operational and the analytics workload. This does not replace the need for a separate data warehouse when you need to integrate data from multiple sources before running the analytics workload or when you require extreme analytics performance using pre-aggregated data such as cubes.
- Do you need the ability to use OLAP cubes?
    - If yes, then you will want an option that provides support for pre-aggregated data. This is typically preferred when providing aggregates helps business users consistently calculate data aggregates in a way that makes sense for your data. Pre-aggregated data can also provide a large performance boost when dealing with several columns across many rows.
- Do you need the ability to integrate data from several sources, beyond your OLTP data store?
    - If so, consider options that easily integrate multiple data sources.

## <a name="matrix"></a> Capability Matrix

### General Capabilities

| | Azure Analysis Services | SQL Server Analysis Services | SQL Server + Columnstore Indexes |
| --- | --- | --- | --- |
| Is managed service | Yes | No | Yes (if using Azure SQL) |
| Supports pre-aggregated data such as cubes | Yes | Yes | No |
| Easily integrate multiple data sources | Yes | Yes | No |
| Supports real-time analytics | No | No | Yes |
| Requires process to copy data from source(s) | Yes | Yes | No |
| Azure Active Directory (AAD) integration | Yes | No | Yes (Azure SQL) |

### Scalability Capabilities

| | Azure Analysis Services | SQL Server Analysis Services | SQL Server + Columnstore Indexes |
| --- | --- | --- | --- |
| Redundant regional servers for high availability  | [Yes](https://docs.microsoft.com/azure/analysis-services/analysis-services-bcdr) | No | Yes (Azure SQL) |
| Supports query scale out  | Yes | No | No |
| Dynamic scalability (scale up)  | Yes | No | Yes (Azure SQL) |

## <a name="wheretogo"></a>Where to go from here
Read Next:
[Data Warehousing Solution Pattern](../solution-patterns/data-warehousing.md)

See Also:

Related Solution Patterns
- Working with transactional data
    - [Online Transaction Processing (OLTP)](../solution-patterns/online-transaction-processing.md)
    - [Online Analytical Processing (OLAP)](../solution-patterns/online-analytical-processing.md)
    - [Data Warehousing](../solution-patterns/data-warehousing.md)

Related Technology Choices
- Transactional data stores
    - [Online Transaction Processing (OLTP) data stores](../technology-choices/oltp-data-stores.md)
    - [Data Warehouses](../technology-choices/data-warehouses.md)
