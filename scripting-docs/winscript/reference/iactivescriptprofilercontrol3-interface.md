---
title: "IActiveScriptProfilerControl3 (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 64bc860a-54d4-475a-80f6-2f9dba6448ee
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptProfilerControl3 (Interfaz)
Proporciona un método para enumerar los objetos del montón GC asociados a un motor de script.  
  
## Sintaxis  
  
```  
interface IActiveScriptProfilerControl3 : IActiveScriptProfilerControl2  
```  
  
## Métodos  
 [IActiveScriptProfilerControl3::EnumHeap \(Método\)](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)  
 Devuelve una interfaz \([IActiveScriptProfilerHeapEnum \(Interfaz\)](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\) que se puede utilizar para recorrer en iteración los objetos del montón GC en el contexto del motor de script asociado.