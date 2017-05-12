---
title: "BREAKREASON (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: BREAKREASON
apilocation: scrobj.dll
helpviewer_keywords: 
  - "BREAKREASON (enumeración)"
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# BREAKREASON (Enumeraci&#243;n)
Indica qué produjo la interrupción.  
  
## Sintaxis  
  
```  
typedef enum tagBREAKREASON {  
   BREAKREASON_STEP,  
   BREAKREASON_BREAKPOINT,  
   BREAKREASON_DEBUGGER_BLOCK,  
   BREAKREASON_HOST_INITIATED,  
   BREAKREASON_LANGUAGE_INITIATED,  
   BREAKREASON_DEBUGGER_HALT,  
   BREAKREASON_ERROR,  
   BREAKREASON_JIT  
} BREAKREASON;  
```  
  
## Members  
  
|Miembro|Descripción|  
|-------------|-----------------|  
|BREAKREASON\_STEP|El motor de lenguaje está en el modo de entrada.|  
|BREAKREASON\_BREAKPOINT|El motor de lenguaje encontró un punto de interrupción explícito.|  
|BREAKREASON\_DEBUGGER\_BLOCK|El motor de lenguaje encontró un bloque del depurador en otro subproceso.|  
|BREAKREASON\_HOST\_INITIATED|El host solicitó una interrupción.|  
|BREAKREASON\_LANGUAGE\_INITIATED|El motor de lenguaje solicitó una interrupción.|  
|BREAKREASON\_DEBUGGER\_HALT|El depurador IDE solicitó una interrupción.|  
|BREAKREASON\_ERROR|Un error de ejecución produjo la interrupción.|  
|BREAKREASON\_JIT|Producido por el inicio de JIT Debugging.|  
  
## Vea también  
 [Active Script Debugger \(Constantes, enumeraciones y estructuras\)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)