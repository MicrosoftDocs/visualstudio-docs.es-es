---
title: "IActiveScriptProfilerControl3::EnumHeap (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 2799d06d-20dd-4c12-9646-554c0ea3606e
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerControl3::EnumHeap (M&#233;todo)
Devuelve una interfaz \([IActiveScriptProfilerHeapEnum \(Interfaz\)](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\) que se puede utilizar para recorrer en iteración los objetos del montón GC en el contexto del motor de script asociado.  
  
 Puede llamar a este método en debug o release el modo.  Se debe llamar a este método cuando el subproceso de la interfaz de usuario está inactivo.  Después de haber llamado al método, las operaciones se deben realizar en el motor de scripts excepto [IActiveScriptProfilerHeapEnum::Next Method](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) hasta que [IActiveScriptProfilerHeapEnum::Next Method](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) devuelve S\_FALSE o se libera el puntero de interfaz de [IActiveScriptProfilerHeapEnum \(Interfaz\)](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) .  
  
## Sintaxis  
  
```  
HRESULT EnumHeap([out] IActiveScriptProfilerHeapEnum** ppEnum);  
  
```  
  
#### Parámetros  
 ppEnum  
 \[out\] Devuelve [IActiveScriptProfilerHeapEnum \(Interfaz\)](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## Valor devuelto  
 HRESULT.