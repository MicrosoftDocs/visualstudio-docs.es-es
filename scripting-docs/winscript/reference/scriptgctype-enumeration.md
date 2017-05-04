---
title: "SCRIPTGCTYPE (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: f289cc7d-2a69-4720-bee0-ea27d054f308
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# SCRIPTGCTYPE (Enumeraci&#243;n)
El tipo de recolección de elementos no utilizados a realizar.  Se usa en el método [IActiveScriptGarbageCollector::CollectGarbage](../../winscript/reference/iactivescriptgarbagecollector-collectgarbage.md).  
  
## Sintaxis  
  
```cpp  
typedef enum tagSCRIPTGCTYPE {  
    SCRIPTGCTYPE_NORMAL           = 0,  
    SCRIPTGCTYPE_EXHAUSTIVE       = 1,  
} SCRIPTGCTYPE;  
  
```  
  
## Valores de enumeración  
  
|||  
|-|-|  
|SCRIPTGCTYPE\_NORMAL|Haga la recolección de elementos no utilizados normal.  El valor entero es 0.|  
|SCRIPTGCTYPE\_EXHAUSTIVE|Haga la recolección de elementos no utilizados completa.  El valor entero es 1.|  
  
## Vea también  
 [Active Script \(constantes, enumeraciones y códigos de error\)](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)