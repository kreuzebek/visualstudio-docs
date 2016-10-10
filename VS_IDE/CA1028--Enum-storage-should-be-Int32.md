---
title: "CA1028: Enum storage should be Int32"
ms.custom: na
ms.date: 10/03/2016
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - vs-devops-test
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
caps.latest.revision: 19
manager: douge
translation.priority.ht: 
  - cs-cz
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pl-pl
  - pt-br
  - ru-ru
  - tr-tr
  - zh-cn
  - zh-tw
---
# CA1028: Enum storage should be Int32
|||  
|-|-|  
|TypeName|EnumStorageShouldBeInt32|  
|CheckId|CA1028|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Cause  
 The underlying type of a public enumeration is not <xref:System.Int32?qualifyHint=True>.  
  
## Rule Description  
 An enumeration is a value type that defines a set of related named constants. By default, the <xref:System.Int32?qualifyHint=True> data type is used to store the constant value. Even though you can change this underlying type, it is not necessary or recommended for most scenarios. Note that no significant performance gain is achieved by using a data type that is smaller than <xref:System.Int32?qualifyHint=False>. If you cannot use the default data type, you should use one of the Common Language System (CLS)-compliant integral types, <xref:System.Byte?qualifyHint=False>, <xref:System.Int16?qualifyHint=False>, <xref:System.Int32?qualifyHint=False>, or <xref:System.Int64?qualifyHint=False> to make sure that all values of the enumeration can be represented in CLS-compliant programming languages.  
  
## How to Fix Violations  
 To fix a violation of this rule, unless size or compatibility issues exist, use <xref:System.Int32?qualifyHint=False>. For situations where <xref:System.Int32?qualifyHint=False> is not large enough to hold the values, use <xref:System.Int64?qualifyHint=False>. If backward compatibility requires a smaller data type, use <xref:System.Byte?qualifyHint=False> or <xref:System.Int16?qualifyHint=False>.  
  
## When to Suppress Warnings  
 Suppress a warning from this rule only if backward compatibility issues require it. In applications, failure to comply with this rule usually does not cause problems. In libraries, where language interoperability is required, failure to comply with this rule might adversely affect your users.  
  
## Example of a Violation  
  
### Description  
 The following example shows two enumerations that do not use the recommended underlying data type.  
  
### Code  
 [!CODE [FxCop.Design.EnumIntegralType#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType#1)]  
  
## Example of How to Fix  
  
### Description  
 The following example fixes the previous violation by changing the underlying data type to <xref:System.Int32?qualifyHint=False>.  
  
### Code  
 [!CODE [FxCop.Design.EnumIntegralTypeFixed#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed#1)]  
  
## Related Rules  
 [CA1008: Enums should have zero value](../VS_IDE/CA1008--Enums-should-have-zero-value.md)  
  
 [CA1027: Mark enums with FlagsAttribute](../VS_IDE/CA1027--Mark-enums-with-FlagsAttribute.md)  
  
 [CA2217: Do not mark enums with FlagsAttribute](../VS_IDE/CA2217--Do-not-mark-enums-with-FlagsAttribute.md)  
  
 [CA1700: Do not name enum values 'Reserved'](../VS_IDE/CA1700--Do-not-name-enum-values--Reserved-.md)  
  
 [CA1712: Do not prefix enum values with type name](../VS_IDE/CA1712--Do-not-prefix-enum-values-with-type-name.md)  
  
## See Also  
 <xref:System.Byte?qualifyHint=True>   
 <xref:System.Int16?qualifyHint=True>   
 <xref:System.Int32?qualifyHint=True>   
 <xref:System.Int64?qualifyHint=True>