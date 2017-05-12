---
title: "IDebugApplication110::AsynchronousCallInMainThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplication110::AsynchronousCallInMainThread"
ms.assetid: 13b80ff0-4bed-48c1-8031-d4147b51bf6c
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugApplication110::AsynchronousCallInMainThread
Realiza una llamada asincrónica en el subproceso principal.  
  
> [!IMPORTANT]
>  [IDebugApplication110 \(Interfaz\)](../../winscript/reference/idebugapplication110-interface.md) es implementado por PDM v11.0 y mayor.  Encontrado en activdbg100.h.  
  
## Sintaxis  
  
```cpp  
HRESULT AsynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
  
```  
  
#### Parámetros  
 `pptc`  
 El objeto de [IDebugThreadCall \(Interfaz\)](../../winscript/reference/idebugthreadcall-interface.md) a la llamada.  
  
 `dwParam1`  
 El primer parámetro de la llamada.  
  
 `dwParam1`  
 El primer parámetro de la llamada.  
  
 `dwParam2`  
 El segundo parámetro de la llamada.  
  
 `dwParam3`  
 El tercer parámetro de la llamada.  
  
## Vea también  
 [IDebugApplication110 \(Interfaz\)](../../winscript/reference/idebugapplication110-interface.md)