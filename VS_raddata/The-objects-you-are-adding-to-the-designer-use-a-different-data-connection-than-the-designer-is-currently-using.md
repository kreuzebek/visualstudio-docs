---
title: "The objects you are adding to the designer use a different data connection than the designer is currently using"
ms.custom: na
ms.date: 10/07/2016
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 3
manager: ghogen
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - ru-ru
  - zh-cn
  - zh-tw
translation.priority.mt: 
  - cs-cz
  - pl-pl
  - pt-br
  - tr-tr
---
# The objects you are adding to the designer use a different data connection than the designer is currently using
The objects you are adding to the designer use a different data connection than the designer is currently using. Do you want to replace the connection used by the designer?  
  
 When you add items to the Object Relational Designer (O/R Designer), all items use one shared data connection. (The design surface represents the <xref:System.Data.Linq.DataContext?qualifyHint=False>, which uses a single connection for all objects on the surface.) If you add an object to the designer that uses a data connection that differs from the data connection currently being used by the designer, this message appears. To resolve this error, you can choose to maintain the existing connection. If you make this choice, the selected object will not be added. Alternatively, you can choose to add the object and reset the <xref:System.Data.Linq.DataContext?qualifyHint=False> connection to the new connection.  
  
> [!NOTE]
>  If you click **Yes**, all entity classes on the O/R Designer are mapped to the new connection.  
  
### To replace the existing connection with the connection used by the selected object  
  
-   Click **Yes**.  
  
     The selected object is added to the O/R Designer, and the DataContext.Connection is set to the new connection.  
  
### To continue to use the existing connection and cancel adding the selected object  
  
-   Click **No**.  
  
     The action is canceled. The DataContext.Connection remains set to the existing connection.  
  
## See Also  
 [LINQ to SQL Tools in Visual Studio](../VS_raddata/LINQ-to-SQL-Tools-in-Visual-Studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Connecting to Data in Visual Studio](../VS_raddata/Connecting-to-Data-in-Visual-Studio.md)