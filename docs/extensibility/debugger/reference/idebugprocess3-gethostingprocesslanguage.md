---
title: "IDebugProcess3::GetHostingProcessLanguage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::GetHostingProcessLanguage"
helpviewer_keywords: 
  - "IDebugProcess3::GetHostingProcessLanguage"
ms.assetid: 52fca002-a9ef-43b1-9192-afbe7bb59ad4
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess3::GetHostingProcessLanguage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método devuelve `GUID` que representa el lenguaje de este proceso como definido por una llamada a [SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md).  
  
## Sintaxis  
  
```cpp  
HRESULT GetHostingProcessLanguage(  
   GUID* pguidLang  
);  
```  
  
```c#  
int GetHostingProcessLanguage(  
   out Guid pguidLang  
);  
```  
  
#### Parámetros  
 `pguidLang`  
 \[out\]  `GUID` de lenguaje de este proceso.  `GUID_NULL` \(C\+\+\) o `Guid.Empty` \(C\#\) significa que el lenguaje no está establecido.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve el código de error.  
  
## Vea también  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)