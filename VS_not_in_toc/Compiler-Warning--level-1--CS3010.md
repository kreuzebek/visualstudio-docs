---
title: "Compiler Warning (level 1) CS3010"
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
ms.assetid: d57bd750-df15-4e6a-9579-66de8b276b7e
caps.latest.revision: 12
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
# Compiler Warning (level 1) CS3010
'member': CLS-compliant interfaces must have only CLS-compliant members  
  
 In an assembly marked with `[assembly:CLCSompliant(true)]`, an interface contains a member marked with `[CLCSompliant(false)]`. Remove one of the Common Language Specification (CLS) compliance attributes. For more information about CLS Compliance, see [<PAVE OVER\> Writing CLS-Compliant Code](assetId:///4c705105-69a2-4e5e-b24e-0633bc32c7f3) and [Language Independence and Language-Independent Components](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Example  
 The following example generates CS3010:  
  
```  
// CS3010.cs  
  
using System;  
  
[assembly:CLSCompliant(true)]  
public interface I  
{  
    [CLSCompliant(false)]  
    int M();   // CS3010  
}  
  
public class C : I  
{  
    public int M()  
    {  
        return 1;  
    }  
  
    public static void Main()  
    {  
    }  
}  
```