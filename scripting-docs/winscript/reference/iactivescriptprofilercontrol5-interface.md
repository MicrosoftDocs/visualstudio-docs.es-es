---
title: "IActiveScriptProfilerControl5 (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 7fd0ce34-6ae3-428f-ba90-3e86a8a98ed0
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# IActiveScriptProfilerControl5 (Interfaz)
Proporciona un método para enumerar los objetos del montón GC asociados a un motor de script.  
  
## Sintaxis  
  
```  
interface IActiveScriptProfilerControl5 : IActiveScriptProfilerControl4  
```  
  
## Métodos  
 [IActiveScriptProfilerControl5::EnumHeap2 \(Método\)](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)  
 Devuelve una interfaz \([IActiveScriptProfilerHeapEnum \(Interfaz\)](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\) que se puede utilizar para recorrer en iteración los objetos del montón GC en el contexto del motor de script asociado.