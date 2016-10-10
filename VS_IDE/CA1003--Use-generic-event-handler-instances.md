---
title: "CA1003: Use generic event handler instances"
ms.custom: na
ms.date: 10/10/2016
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - vs-devops-test
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: 22
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
# CA1003: Use generic event handler instances
|||  
|-|-|  
|TypeName|UseGenericEventHandlerInstances|  
|CheckId|CA1003|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Cause  
 A type contains a delegate that returns void, whose signature contains two parameters (the first an object and the second a type that is assignable to EventArgs), and the containing assembly targets .NET Framework 2.0.  
  
## Rule Description  
 Before .NET Framework 2.0, in order to pass custom information to the event handler, a new delegate had to be declared that specified a class that was derived from the <xref:System.EventArgs?qualifyHint=True> class. This is no longer true in .NET Framework 2.0, which introduced the <xref:System.EventHandler`1?qualifyHint=True> delegate. This generic delegate allows any class that is derived from <xref:System.EventArgs?qualifyHint=False> to be used together with the event handler.  
  
## How to Fix Violations  
 To fix a violation of this rule, remove the delegate and replace its use by using the <xref:System.EventHandler`1?qualifyHint=True> delegate. If the delegate is autogenerated by the Visual Basic compiler, change the syntax of the event declaration to use the <xref:System.EventHandler`1?qualifyHint=True> delegate.  
  
## When to Suppress Warnings  
 Do not suppress a warning from this rule.  
  
## Example  
 The following example shows a delegate that violates the rule. In the Visual Basic example, comments describe how to modify the example to satisfy the rule. For the C# example, an example follows that shows the modified code.  
  
 [!CODE [FxCop.Design.CustomEventHandler#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler#1)]  
  
## Example  
 The following example removes the delegate declaration from the previous example, which satisfies the rule, and replaces its use in the `ClassThatRaisesEvent` and `ClassThatHandlesEvent` methods by using the <xref:System.EventHandler`1?qualifyHint=True> delegate.  
  
 [!CODE [FxCop.Design.GenericEventHandler#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.GenericEventHandler#1)]  
  
## Related Rules  
 [CA1005: Avoid excessive parameters on generic types](../VS_IDE/CA1005--Avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Collections should implement generic interface](../VS_IDE/CA1010--Collections-should-implement-generic-interface.md)  
  
 [CA1000: Do not declare static members on generic types](../VS_IDE/CA1000--Do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: Do not expose generic lists](../VS_IDE/CA1002--Do-not-expose-generic-lists.md)  
  
 [CA1006: Do not nest generic types in member signatures](../VS_IDE/CA1006--Do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: Generic methods should provide type parameter](../VS_IDE/CA1004--Generic-methods-should-provide-type-parameter.md)  
  
 [CA1007: Use generics where appropriate](../VS_IDE/CA1007--Use-generics-where-appropriate.md)  
  
## See Also  
 [Generics](../Topic/Generics%20\(C%23%20Programming%20Guide\).md)