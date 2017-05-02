---
title: "IDebugApplicationThread110::AsynchronousCallIntoThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 06b3031a-4aec-4a47-afaa-04642a4c4870
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# IDebugApplicationThread110::AsynchronousCallIntoThread
Realiza una llamada asincrónica en el subproceso principal.  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110 \(Interfaz\)](../../winscript/reference/idebugapplicationthread110-interface.md) es implementado por PDM v11.0 y mayor.  Encontrado en activdbg100.h.  
  
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