# FAQ

### Sub-resource of Services

The Sub-resources are case-sentitive and are used when creating private
endpoints. The AVM modules are settting this field automatically, i.e. ["vault"]
for a key vault or ["blob"] for a Blob Storage. For terraform, this field is
optional for `azurerm_private_endpoint`.

```hcl
resource "azurerm_private_endpoint" "example" {
  name                = "example-endpoint"
  location            = azurerm_resource_group.example.location
  resource_group_name = azurerm_resource_group.example.name
  subnet_id           = azurerm_subnet.endpoint.id

  private_service_connection {
    name                           = "example-privateserviceconnection"
    private_connection_resource_id = azurerm_key_vault.example.id
    is_manual_connection           = false
    sub_resource_names             = ["vault"] # Optional, can be
  }
}
```

Private-link resource name | Resource type | Sub-resources
--- | --- | ---
Application Gateway | Microsoft.Network/applicationgateways | Frontend IP Configuration name
Azure AI Search | Microsoft.Search/searchServices | searchService
Azure AI services | Microsoft.CognitiveServices/accounts | account
Azure API for FHIR (Fast Healthcare Interoperability Resources) | Microsoft.HealthcareApis/services | fhir
Azure API Management | Microsoft.ApiManagement/service | Gateway
Azure App Configuration | Microsoft.Appconfiguration/configurationStores | configurationStores
Azure App Service | Microsoft.Web/hostingEnvironments | hosting environment
Azure App Service | Microsoft.Web/sites | sites
Azure Attestation Service | Microsoft.Attestation/attestationProviders | standard
Azure Automation | Microsoft.Automation/automationAccounts | Webhook, DSCAndHybridWorker
Azure Backup | Microsoft.RecoveryServices/vaults | AzureBackup, AzureSiteRecovery
Azure Batch | Microsoft.Batch/batchAccounts | batchAccount, nodeManagement
Azure Cache for Redis | Microsoft.Cache/Redis | redisCache
Azure Cache for Redis Enterprise | Microsoft.Cache/redisEnterprise | redisEnterprise
Azure Container Apps | Microsoft.App/ManagedEnvironments | managedEnvironments
Azure Container Registry | Microsoft.ContainerRegistry/registries | registry
Azure Cosmos DB | Microsoft.AzureCosmosDB/databaseAccounts | SQL, MongoDB, Cassandra, Gremlin, Table
Azure Cosmos DB for MongoDB vCore | Microsoft.DocumentDb/mongoClusters | mongoCluster
Azure Cosmos DB for PostgreSQL | Microsoft.DBforPostgreSQL/serverGroupsv2 | coordinator
Azure Data Explorer | Microsoft.Kusto/clusters | cluster
Azure Data Factory | Microsoft.DataFactory/factories | dataFactory
Azure Database for MariaDB | Microsoft.DBforMariaDB/servers | mariadbServer
Azure Database for MySQL - Flexible Server | Microsoft.DBforMySQL/flexibleServers | mysqlServer
Azure Database for MySQL - Single Server | Microsoft.DBforMySQL/servers | mysqlServer
Azure Database for PostgreSQL - Flexible server | Microsoft.DBforPostgreSQL/flexibleServers | postgresqlServer
Azure Database for PostgreSQL - Single server | Microsoft.DBforPostgreSQL/servers | postgresqlServer
Azure Databricks | Microsoft.Databricks/workspaces | databricks_ui_api, browser_authentication
Azure Device Provisioning Service | Microsoft.Devices/provisioningServices | iotDps
Azure Digital Twins | Microsoft.DigitalTwins/digitalTwinsInstances | API
Azure Event Grid | Microsoft.EventGrid/domains | domain
Azure Event Grid | Microsoft.EventGrid/topics | topic
Azure Event Hub | Microsoft.EventHub/namespaces | namespace
Azure File Sync | Microsoft.StorageSync/storageSyncServices | File Sync Service
Azure HDInsight | Microsoft.HDInsight/clusters | cluster
Azure IoT Central | Microsoft.IoTCentral/IoTApps | IoTApps
Azure IoT Hub | Microsoft.Devices/IotHubs | iotHub
Azure Key Vault | Microsoft.KeyVault/vaults | vault
Azure Key Vault HSM (hardware security module) | Microsoft.Keyvault/managedHSMs | HSM
Azure Kubernetes Service - Kubernetes API | Microsoft.ContainerService/managedClusters | management
Azure Machine Learning | Microsoft.MachineLearningServices/registries | amlregistry
Azure Machine Learning | Microsoft.MachineLearningServices/workspaces | amlworkspace
Azure Managed Disks | Microsoft.Compute/diskAccesses | managed disk
Azure Media Services | Microsoft.Media/mediaservices | keydelivery, liveevent, streamingendpoint
Azure Migrate | Microsoft.Migrate/assessmentProjects | project
Azure Monitor Private Link Scope | Microsoft.Insights/privatelinkscopes | azuremonitor
Azure Relay | Microsoft.Relay/namespaces | namespace
Azure Service Bus | Microsoft.ServiceBus/namespaces | namespace
Azure SignalR Service | Microsoft.SignalRService/SignalR | signalr
Azure SignalR Service | Microsoft.SignalRService/webPubSub | webpubsub
Azure SQL Database | Microsoft.Sql/servers | SQL Server (sqlServer)
Azure SQL Managed Instance | Microsoft.Sql/managedInstances | managedInstance
Azure Static Web Apps | Microsoft.Web/staticSites | staticSites
Azure Storage | Microsoft.Storage/storageAccounts | Blob (blob, blob_secondary), Table (table, table_secondary), Queue (queue, queue_secondary), File (file, file_secondary), Web (web, web_secondary), Dfs (dfs, dfs_secondary)
Azure Synapse | Microsoft.Synapse/privateLinkHubs | web
Azure Synapse Analytics | Microsoft.Synapse/workspaces | Sql, SqlOnDemand, Dev
Azure AI Video Indexer | Microsoft.VideoIndexer/accounts | account
Azure Virtual Desktop - host pools | Microsoft.DesktopVirtualization/hostpools | connection
Azure Virtual Desktop - workspaces | Microsoft.DesktopVirtualization/workspaces | feed, global
Device Update for IoT Hub | Microsoft.DeviceUpdate/accounts | DeviceUpdate
Integration Account (Premium) | Microsoft.Logic/integrationAccounts | integrationAccount
Microsoft Purview | Microsoft.Purview/accounts | account
Microsoft Purview | Microsoft.Purview/accounts | portal
Power BI | Microsoft.PowerBI/privateLinkServicesForPowerBI | Power BI
Private Link service (your own service) | Microsoft.Network/privateLinkServices | empty
Resource Management Private Links | Microsoft.Authorization/resourceManagementPrivateLinks | ResourceManagement

Sources:

- [What is a  private endpoint?](https://learn.microsoft.com/en-us/azure/private-link/private-endpoint-overview#private-link-resource)
- [azurerm_private_endpoint](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/private_endpoint)]
