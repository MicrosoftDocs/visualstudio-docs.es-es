---
title: "IActiveScriptGarbageCollector::CollectGarbage | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptGarbageCollector::CollectGarbage
El host de script activo llama a este método para iniciar la recolección de elementos no utilizados.  
  
## Sintaxis  
  
```  
HRESULT CollectGarbage(  
        SCRIPTGCTYPE scriptgctype  
    );  
  
```  
  
#### Parámetros  
 `scriptgctype`  
 \[in\] [SCRIPTGCTYPE \(Enumeración\)](../../winscript/reference/scriptgctype-enumeration.md) que especifica si hacer la recolección de elementos no utilizados normal o exhaustiva.  
  
## Valor devuelto  
 Devuelve un HRESULT.  
  
## Vea también  
 [IActiveScriptGarbageCollector \(Interfaz\)](../../winscript/reference/iactivescriptgarbagecollector-interface.md)