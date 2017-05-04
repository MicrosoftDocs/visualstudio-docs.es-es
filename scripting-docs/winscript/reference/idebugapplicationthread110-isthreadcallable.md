---
title: "IDebugApplicationThread110::IsThreadCallable | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread110::IsThreadCallable"
ms.assetid: 2a75a366-801d-47e0-bba3-51aa669e03a7
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationThread110::IsThreadCallable
Determina si este subproceso está en un estado que procesa las llamadas realizadas utilizando los mecanismos de conmutación de subproceso de PDM, como SynchronousCallInThread.  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110 \(Interfaz\)](../../winscript/reference/idebugapplicationthread110-interface.md) es implementado por PDM v11.0 y mayor.  Encontrado en activdbg100.h.  
  
## Sintaxis  
  
```cpp  
HRESULT IsThreadCallable([out, annotation("_Out_")] BOOL * pfIsCallable);  
```  
  
#### Parámetros  
 `pfIsCallable`  
 \[out\] `true` si el subproceso es accesible, si no `false`.  
  
## Vea también  
 [IDebugApplicationThread110 \(Interfaz\)](../../winscript/reference/idebugapplicationthread110-interface.md)