---
title: "IDebugProgramProvider2"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: na
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramProvider2"
helpviewer_keywords: 
  - "IDebugProgramProvider2 interface"
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
translation.priority.mt: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---
# IDebugProgramProvider2
This registered interface allows the session debug manager (SDM) to obtain information about programs that have been "published" through the [IDebugProgramPublisher2](../extensibility/idebugprogrampublisher2.md) interface.  
  
## Syntax  
  
```  
IDebugProgramProvider2 : IUnknown  
```  
  
## Notes for Implementers  
 The debug engine (DE) implements this interface to provide information about programs being debugged. This interface is registered in the DE section of the registry using the metric `metricProgramProvider`, as described in [SDK Helpers for Debugging](../extensibility/sdk-helpers-for-debugging.md).  
  
## Notes for Callers  
 Call COM's `CoCreateInstance` function with the `CLSID` of the program provider that is obtained from the registry. See the Example.  
  
## Methods in Vtable order  
  
|Method|Description|  
|------------|-----------------|  
|[GetProviderProcessData](../extensibility/idebugprogramprovider2--getproviderprocessdata.md)|Obtains information about programs running, filtered in a variety of ways.|  
|[GetProviderProgramNode](../extensibility/idebugprogramprovider2--getproviderprogramnode.md)|Gets a program node, given a specific process ID.|  
|[WatchForProviderEvents](../extensibility/idebugprogramprovider2--watchforproviderevents.md)|Establishes a callback to watch for provider events associated with specific kinds of processes.|  
|[SetLocale](../extensibility/idebugprogramprovider2--setlocale.md)|Establishes a locale for any language-specific resources needed by the DE.|  
  
## Remarks  
 Normally, a process uses this interface to find out about the programs running in that process.  
  
## Requirements  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Example  
  
```cpp#  
IDebugProgramProvider2 *GetProgramProvider(GUID *pDebugEngineGuid)  
{  
    // This is typically defined globally.  For this example, it is  
    // defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugProgramProvider2 *pProvider = NULL;  
    if (pDebugEngineGuid != NULL) {  
        CLSID clsidProvider = { 0 };  
        ::GetMetric(NULL,  
                    metrictypeEngine,  
                    *pDebugEngineGuid,  
                    metricProgramProvider,  
                    &clsidProvider,  
                    strRegistrationRoot);  
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {  
            CComPtr<IDebugProgramProvider2> spProgramProvider;  
            spProgramProvider.CoCreateInstance(clsidProvider);  
            if (spProgramProvider != NULL) {  
                pProvider = spProgramProvider.Detach();  
            }  
        }  
    }  
    return(pProvider);  
}  
```  
  
## See Also  
 [Core Interfaces](../extensibility/core-interfaces.md)   
 [IDebugProgramPublisher2](../extensibility/idebugprogrampublisher2.md)   
 [SDK Helpers for Debugging](../extensibility/sdk-helpers-for-debugging.md)