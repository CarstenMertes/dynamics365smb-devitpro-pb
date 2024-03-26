---
title: Using FlowFilters in OData URIs
description: Learn how to use FlowFilter expressions in OData URIs.
ms.custom: bap-template
ms.date: 01/28/2024
ms.reviewer: jswymer
ms.topic: conceptual
---
# Using FlowFilters in OData URIs

You can set FlowFilters on the data that your OData web service extracts from the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] database.  
  
FlowFilters are a special kind of filter that you use to set ranges on calculations that are shown in FlowFields. For more information, see [FlowFilter Overview](../developer/devenv-flowfilter-overview.md). FlowFilters for a page are included in the metadata for that page when it is published as a web service. You can then use FlowFilters as filters in a URI that specifies a query against page data. However, only those FlowFilters that are required to calculate the FlowFields that are exposed on the page as controls are included.  
  
## Use FlowFilters to Query Data on the Item Card Page

In this procedure, you create and publish a web service from the **Item Card** page in [!INCLUDE[prod_short](../developer/includes/prod_short.md)] and then query the data in that web service by using a FlowFilter.  
  
1. Register and publish a page web service by using the [!INCLUDE[nav_web_md](../developer/includes/nav_web_md.md)]. See [Publishing a Web Service](publish-web-service.md).

    Register and publish page 30, Item Card, and name the service **ItemCard**. 
  
2. Start an internet browser, then in the **Address** field, enter a URI in this format:  
  
    ```http  
    https://<Server>:<WebServicePort>/<ServerInstance>/ODataV4/$metadata  
    ```  
  
     If [!INCLUDE[server](../developer/includes/server.md)] is running on the local computer and uses the default [!INCLUDE[server](../developer/includes/server.md)] instance and the default OData port, then the address is:  
  
    ```http  
    https://localhost:7048/BC230/ODataV4/$metadata  
    ```  
  
3. Examine the metadata that is returned by this URI. At the end of the list is a set of parameters that end in the word `Filter`. This is the list of FlowFilters for the page:  
  
    ```json  
    <Property Type="Edm.String" Name="Location_Filter" Nullable="true"/>  
    <Property Type="Edm.String" Name="Drop_Shipment_Filter" Nullable="true"/>  
    <Property Type="Edm.String" Name="Variant_Filter" Nullable="true"/>  
    <Property Type="Edm.String" Name="Lot_No_Filter" Nullable="true"/>  
    <Property Type="Edm.String" Name="Serial_No_Filter" Nullable="true"/>  
    <Property Type="Edm.String" Name="Date_Filter" Nullable="true"/>  
    ```  
  
    > [!NOTE]  
    >  The set of FlowFilters that is listed in the page metadata may not match the set of FlowFilters on the equivalent page in the [!INCLUDE[nav_web_md](../developer/includes/nav_web_md.md)]. This is because the [!INCLUDE[nav_web_md](../developer/includes/nav_web_md.md)] shows all FlowFilter fields that are defined on the table on which the page is based. The metadata only shows the FlowFilters that are used to calculate the FlowField controls that are exposed on the page.  
  
4. Create a URI that returns information for a single item card. For example:  
  
    ```http  
    https://localhost:7048/BC230/ODataV4/Company('CRONUS-International-Ltd.')/ItemCard('1906-S')  
    ```  
  
    This is the "ATHENS Mobile Pedestal" item. The value for the *Qty\_on\_Sales\_Order* parameter is 33:  
  
    ```json  
    "Qty_on_Purch_Order": 20
    ```  
  
5. Apply a FlowFilter to that item and specify **GREEN** as the value for the **Location\_Filter**:  
  
    ```http  
    https://localhost:7048/BC230/ODataV4/Company('CRONUS-International-Ltd.')/ItemCard('1906-S')?$filter=Location_Filter eq 'GREEN'  
    ```  
  
    The item is returned as before, the value of the FlowField that has changed. The value for the *Qty\_on\_Sales\_Order* parameter is now 27:  
  
    ```json 
    "Qty_on_Purch_Order": 27  
    ```  
  
     This indicates that there are 27 ATHENS Mobile Pedestals on sales orders designated for the GREEN location.  
  
## See Also  
 [OData Web Services](OData-Web-Services.md)
