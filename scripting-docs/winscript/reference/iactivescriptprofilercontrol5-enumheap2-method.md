---
title: "IActiveScriptProfilerControl5::EnumHeap2 (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a25859eb-ac28-4a97-bcb3-33788982a76b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IActiveScriptProfilerControl5::EnumHeap2 (M&#233;todo)
Devuelve una interfaz \([IActiveScriptProfilerHeapEnum \(Interfaz\)](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\) que se puede utilizar para recorrer en iteración los objetos del montón GC en el contexto del motor de script asociado.  
  
 Puede llamar a este método en modo de depuración o de lanzamiento.  Se debe llamar a este método cuando el subproceso de la interfaz de usuario está inactivo.  Después de haber llamado al método, no se deben realizar operaciones en el motor de scripts excepto [IActiveScriptProfilerHeapEnum::Next Method](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) hasta que [IActiveScriptProfilerHeapEnum::Next Method](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) devuelven S\_FALSE o se libera el puntero de interfaz [IActiveScriptProfilerHeapEnum \(Interfaz\)](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## Sintaxis  
  
```  
HRESULT EnumHeap2(  
    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,  
    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
  
```  
  
#### Parámetros  
 enumFlags  
 Valor que especifica si la información adicional sobre un objeto designado en una relación del objeto está expuesta.  La información adicional puede indicar a si el objeto al que apunta es un método get o set.  Para obtener más información, vea [PROFILER\_HEAP\_ENUM\_FLAGS \(Enumeración\)](../../winscript/reference/profiler-heap-enum-flags-enumeration.md).  
  
 ppEnum  
 \[out\] Devuelve [IActiveScriptProfilerHeapEnum \(Interfaz\)](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## Valor devuelto  
 Devuelve un HRESULT.  Los valores posibles son:  
  
|Valor devuelto|Significado|  
|--------------------|-----------------|  
|`S_OK`|La enumeración de pila completa correctamente.|  
|`E_OUTOFMEMORY`|No hay suficiente memoria disponible realizar la enumeración de pila.|  
|`E_FAIL`|Error interno.|