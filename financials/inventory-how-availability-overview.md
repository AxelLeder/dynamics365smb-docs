---
title: 'How to: Get an Availability Overview| Microsoft Docs'
description: Describes how to view the availability of items across locations, per sales or purchase events, by a time period, or by the item's position on an assembly BOM.
documentationcenter: ''
author: SorenGP

ms.service: dynamics365-financials
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: stock
ms.date: 03/28/2017
ms.author: SorenGP

---
# How to: Get an Availability Overview
From the context of a business task, you can get advanced information about when and where an item is available, such as when talking to a customer about a delivery date.

You can view the availability of all items per location, and you can view the availability of each item by event, by period, or by location. An event is any scheduled item transaction, such as a sales shipment or an inbound transfer receipt.

**Note**: Availability views by location require that you maintain inventory at more than one location. For more information, see [How to: Set Up Locations](inventory-how-setup-locations.md).

In [Using [!INCLUDE[d365fin](includes/d365fin_md.md)], availability figures are shown in two different fields, each with a different definition:

* The **Quantity on Hand** field shows the actual quantity today according to posted item ledger entries.
* The **Projected Available Balance** field is calculated and shows the quantity on hand plus scheduled receipts minus gross requirements. (In [Using [!INCLUDE[d365fin](includes/d365fin_md.md)], scheduled receipts include quantities on purchase orders and inbound transfer orders. Gross requirements include quantities on sales orders and outbound transfer orders.)

**Tip**: The projected available balance is especially relevant to view in the **Item Availability by Periods** and **Item Availability by Event** windows as they contain the date dimension.  

**Note**: The following procedures describe how to view advanced availability information from the items list and item card. You can also access the information from sales document lines, for the item on the line. For more information, see [How to: Sell Products](sales-how-sell-products.md).

## To view the availability of an item according to when it will be received or shipped
You view the availability of an item according to scheduled item transactions in the **Availability by Event** window.

1. In the top right corner, choose the **Search for Page or Report** icon ![Search for Page or Report](media/ui-search/search_small.png "Search for Page or Report icon"), enter **Items**, and then choose the related link.
2. Open the card of an item that you want to view availability for.
3. Choose the **Item Availability by** action, and then choose the **Event** action.

    The **Item Availability by Event** window shows how the inventory quantity of the item will develop over time according scheduled shipment and receipt events. The window gives a condensed view that shows one line of accumulated information per time interval in which inventory quantities change. Time intervals where no events occurred are not shown. You can expand each line to show details about the event or events that caused the accumulated quantity on the line.
4. Choose the value in the **Projected Available Balance** field to view the item ledger entries or open documents that make up the value.

## To view the availability of an item in different periods
You view the availability of an item over time for specified time periods in the **Item Availability by Periods** window.

1. In the top right corner, choose the **Search for Page or Report** icon ![Search for Page or Report](media/ui-search/search_small.png "Search for Page or Report icon"), enter **Items**, and then choose the related link.
2. Open the card of an item that you want to view availability for.
3. Choose the **Item Availability by** action, and then choose the **Period** action.

    The **Item Availability by Periods** window shows how the inventory quantity of the item will develop over time, shown for a period that you select, such as Day, Week, or Quarter.
4. Choose the value in the **Projected Available Balance** field to view the item ledger entries or open documents that make up the value.

## To view the availability of an item at the locations where it is stored
You view the availability of an item at the different places where it is stored in the **Item Availability by Location** window.

1. In the top right corner, choose the **Search for Page or Report** icon ![Search for Page or Report](media/ui-search/search_small.png "Search for Page or Report icon"), enter **Items**, and then choose the related link.
2. Open the card of an item that you want to view availability for.
3. Choose the **Item Availability by** action, and then choose the **Location** action.

    The **Item Availability by Location** window shows how the inventory quantity of the item will develop in the future, shown for each location where it is stored.
4. Choose the value in the **Qty. on Hand** field to view the item ledger entries that make up the value.
5. Choose the value in the **Projected Available Balance** field to view the item ledger entries or open documents that make up the value.

## To view the availability of all items by the location where they are stored
You view the availability of all your items across all your locations in the **Items by Location** window.

1. In the top right corner, choose the **Search for Page or Report** icon ![Search for Page or Report](media/ui-search/search_small.png "Search for Page or Report icon"), enter **Items**, and then choose the related link.
2. Choose the **Items by Location** action.

    The **Items by Location** window shows for all your items how many are available at each location.
3. Choose the value in the **Qty. on Hand** field to view the item ledger entries that make up the value.

## To view the availability of an item by its use in assembly BOMs
If an item exists in assembly BOMs, either as a parent item or as a component, then you can view how many units of its are required in the **Item Availability by BOM Level** window. The window shows how many units of a parent you can make based on the availability of child items on underlying lines. Any item that has an assembly BOM is shown in the window as a collapsible line. You can expand this line to see the underlying components and lower-level subassemblies with their own BOMs.

You can use the window to find out whether you can fulfill a sales order for an item on a specified date by looking at its current availability and the quantities that can be supplied by its components. You can also use the window to identify bottlenecks in related assembly BOMs.

On each line in the window for both parent items and child items, the following key fields specify the availability figures. You can use these figures to promise how many units of a parent you can supply if you start the related assembly process.

|Field|Description|
|------|-----------|
|**Able to Make Parent**|Shows how many units of any subassembly in the top item you can make. The field specifies how many immediate parent units you can assemble. The value is based on availability of the item on the line.|
|**Able to Make Top Item**|Shows how many units of the top item you can make. The field specifies how many units of the top-line BOM item you can assemble. The value is based on availability of the item on the line.|

The **Item Availability by BOM Level** window shows information for the item on the card or document line that the window is opened for. The item is always shown on the top line. You can view information for other items or for all items by changing the value in the **Item Filter** field.

**Note**: By default, availability figures on the lines show the total availability of all items under the top item. These figures are displayed in the **Available Quantity** field, and the focus is on the top item. However, information about how many subassemblies you can make may be skewed. To get a true indication of how many of the shown subassemblies you can make, you must clear the **Show Total Availability** chack box and then see the figure in the **Able to Make Parent** field.

The **Bottleneck** field specifies which item in the BOM structure restricts you from making a larger quantity than the quantity that is shown in the **Able to Make Top Item** field. For example, the bottleneck item can be a purchased component with an expected receipt date that is too late to make additional units of the top item by the date in the **Needed by Date** field.

## See Also
[Manage Inventory](inventory-manage-inventory.md)  
[How to: Work with Bills of Materials](inventory-how-work-BOMs.md)    
[How to: Set Up Locations](inventory-how-setup-locations.md)  
[How to: Transfer Inventory Between Locations](inventory-how-transfer-between-locations.md)  
[How to: Sell Products](sales-how-sell-products.md)      
[Supply Chain](madeira-supply-chain.md)  
[Working With Financials](ui-work-product.md)  
[General Business Functionality](ui-across-business-areas.md)
