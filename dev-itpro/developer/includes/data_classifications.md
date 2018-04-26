|  Data classification  |  Description  |  Example  |
|---------|---------------|-----------|
|CustomerContent|Content directly provided/created by admins and users.|<ul><li>Customer generated BLOB or structured storage data</li><li>Customer-owned/provided secrets (passwords, certificates, encryption keys, storage keys)</li></ul>|
|EndUserIdentifiableInformation|(EUII) Data that identifies or could be used to identify the user of a Microsoft service. EUII does not contain Customer content.|<ul><li>User name or display name (DOMAIN\UserName)</li><li>User principle name (name@company.com)</li><li>User-specific IP address</li></ul>| 
|AccountData|Customer billing information and payment instrument information, including administrator contact information, such as tenant administrator’s name, address, or phone number.|<ul><li>Tenant administrator contact information (for example, tenant administrator’s name, address, e-mail address, phone number)</li><li>Customer’s provisioning information</li></ul>|  
|EndUsePseudonymousIdentifiers|(EUPI) An identifier created by Microsoft tied to the user of a Microsoft service. When EUPI is combined with other information, such as a mapping table, it identifies the end user. EUPI does not contain information uploaded or created by the customer (Customer content or EUII)|<ul><li>User GUIDs, PUIDs, or SIDs</li><li>Session IDs</li></ul>|
|OrganizationIdentifiableInformation|(OII) Data that can be used to identify a tenant, generally config or usage data. This data is not linkable to a user and does not contain Customer content.|<ul><li>Tenant ID (non-GUID)</li><li>Domain name in e-mail address (xxx@contoso.com) or other tenant-specific domain information</li></ul>| 
|SystemMetadata|Data generated while running the service or program that is not linkable to a user or tenant. |<ul><li>Database table names, database column names, entity names</li></ul>| 