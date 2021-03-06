---
title: "How to: Use Environment Variables in a Build | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "environment variables, referencing"
  - "projects [.NET Framework], environment variables"
  - "MSBuild, environment variables"
ms.assetid: 7f9e4469-8865-4b59-aab3-3ff26bd36e77
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Use Environment Variables in a Build
When you build projects, it is often necessary to set build options using information that is not in the project file or the files that comprise your project. This information is typically stored in environment variables.  
  
## Referencing Environment Variables  
 All environment variables are available to the [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) project file as properties.  
  
> [!NOTE]
>  If the project file contains an explicit definition of a property that has the same name as an environment variable, the property in the project file overrides the value of the environment variable.  
  
#### To use an environment variable in an MSBuild project  
  
-   Reference the environment variable the same way you would a variable declared in your project file. For example, the following code references the BIN_PATH environment variable:  
  
     `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`  
  
 You can use a `Condition` attribute to provide a default value for a property if the environment variable was not set.  
  
#### To provide a default value for a property  
  
-   Use a `Condition` attribute on a property to set the value only if the property has no value. For example, the following code sets the `ToolsPath` property to c:\tools only if the `ToolsPath` environment variable is not set:  
  
     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`  
  
    > [!NOTE]
    >  Property names are not case-sensitive so both `$(ToolsPath)` and `$(TOOLSPATH)` reference the same property or environment variable.  
  
## Example  
 The following project file uses environment variables to specify the location of directories.  
  
```xml  
<Project DefaultTargets="FakeBuild">  
    <PropertyGroup>  
        <FinalOutput>$(BIN_PATH)\myassembly.dll</FinalOutput>  
        <ToolsPath Condition=" '$(ToolsPath)' == '' ">  
            C:\Tools  
        </ToolsPath>  
    </PropertyGroup>  
    <Target Name="FakeBuild">  
        <Message Text="Building $(FinalOutput) using the tools at $(ToolsPath)..."/>  
    </Target>  
</Project>  
```  
  
## See Also  
    [MSBuild ](../msbuild/msbuild.md)
    [MSBuild Properties](../msbuild/msbuild-properties.md)
 [How to: Build the Same Source Files with Different Options](../msbuild/how-to-build-the-same-source-files-with-different-options.md)