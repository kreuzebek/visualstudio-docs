---
title: "MSBuild Error MSB4140"
ms.custom: na
ms.date: 10/01/2016
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-csharp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 13546558-4ed4-44c2-89a6-f69a2b43ed07
caps.latest.revision: 8
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
# MSBuild Error MSB4140
**MSB4140: Default ToolsVersion is specified in neither the registry nor configuration file.**  
  
 The project does not specify a default `ToolsVersion` value. Therefore, MSBuild does not know which value to use.  
  
### To correct this error  
  
-   Make sure that a `DefaultToolsVersion` value is specified either in the registry where Toolsets are defined, or in a configuration file (such as msbuild.exe.config).  
  
## See Also  
 [Standard and Custom Toolset Configurations](../VS_IDE/Standard-and-Custom-Toolset-Configurations.md)   
 [Project Element (MSBuild)](../VS_IDE/Project-Element--MSBuild-.md)   
 [Additional Resources](../VS_IDE/Additional-MSBuild-Resources.md)