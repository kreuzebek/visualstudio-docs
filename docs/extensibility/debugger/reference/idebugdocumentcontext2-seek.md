---
title: "IDebugDocumentContext2::Seek | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentContext2::Seek"
helpviewer_keywords: 
  - "IDebugDocumentContext2::Seek"
ms.assetid: 71501356-8a82-4d36-b354-6625bdd2baa0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentContext2::Seek
Moves the document context by a given number of statements or lines.  
  
## Syntax  
  
```cpp  
HRESULT Seek(   
   int                      nCount,  
   IDebugDocumentContext2** ppDocContext  
);  
```  
  
```cpp  
int Seek(   
   int                        nCount,  
   out IDebugDocumentContext2 ppDocContext  
);  
```  
  
#### Parameters  
 `nCount`  
 [in] The number of statements or lines to move ahead, depending on the document context.  
  
 `ppDocContext`  
 [out] Returns a new [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) object with the new position.  
  
## Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## See Also  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)