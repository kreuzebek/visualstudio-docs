---
title: "Compiler Error CS0272"
ms.custom: na
ms.date: 10/01/2016
ms.devlang: 
  - CSharp
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-csharp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 16a9aab6-922a-45a3-a0ef-f32e99f3950f
caps.latest.revision: 11
manager: douge
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
# Compiler Error CS0272
The property or indexer 'property/indexer' cannot be used in this context because the set accessor is inaccessible  
  
 This error occurs when the `set` accessor is not accessible to the program code. To resolve this error, increase the accessibility of the accessor, or change the calling location. For more information, see [Restricting Accessor Accessibility](../Topic/Restricting%20Accessor%20Accessibility%20\(C%23%20Programming%20Guide\).md).  
  
## Example  
 The following example generates CS0272:  
  
```  
// CS0272.cs  
public class MyClass  
{  
    public int Property  
    {  
        get { return 0; }  
        private set { }  
    }  
}  
  
public class Test  
{  
    static void Main()  
    {  
        MyClass c = new MyClass();  
        c.Property = 10;      // CS0272  
        // To resolve, remove the previous line   
        // or use an appropriate modifier on the set accessor.  
    }  
}  
```