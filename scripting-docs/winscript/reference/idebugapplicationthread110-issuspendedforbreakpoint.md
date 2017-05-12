---
title: "IDebugApplicationThread110::IsSuspendedForBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread110::IsSuspendedForBreakPoint"
ms.assetid: 60688222-557f-4a43-a19b-846cee393cd0
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationThread110::IsSuspendedForBreakPoint
Determina si [IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) se ha asignado este subproceso y aún no ha finalizado.  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110 \(Interfaz\)](../../winscript/reference/idebugapplicationthread110-interface.md) es implementado por PDM v11.0 y mayor.  Encontrado en activdbg100.h.  
  
## Sintaxis  
  
```cpp  
HRESULT IsSuspendedForBreakPoint([out, annotation("_Out_")] BOOL * pfIsSuspended);  
```  
  
#### Parámetros  
 `pfIsSuspended`  
 \[out\] `true` si se suspende el subproceso para un punto de interrupción, si no `false`.  
  
## Vea también  
 [IDebugApplicationThread110 \(Interfaz\)](../../winscript/reference/idebugapplicationthread110-interface.md)