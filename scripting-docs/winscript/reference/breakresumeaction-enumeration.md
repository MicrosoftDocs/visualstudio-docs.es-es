---
title: "BREAKRESUMEACTION (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: BREAKRESUMEACTION
apilocation: scrobj.dll
helpviewer_keywords: 
  - "BREAKRESUMEACTION (enumeración)"
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# BREAKRESUMEACTION (Enumeraci&#243;n)
Describe cómo continuar desde un punto de interrupción.  
  
## Sintaxis  
  
```  
typedef enum tagBREAKRESUME_ACTION {    BREAKRESUMEACTION_ABORT,    BREAKRESUMEACTION_CONTINUE,    BREAKRESUMEACTION_STEP_INTO,    BREAKRESUMEACTION_STEP_OVER,    BREAKRESUMEACTION_STEP_OUT,    BREAKRESUMEACTION_IGNORE,    BREAKRESUMEACTION_STEP_DOCUMENT, } BREAKRESUMEACTION;  
```  
  
## Miembros  
  
|Miembro|Descripción|  
|-------------|-----------------|  
|BREAKRESUMEACTION\_ABORT|Anula la aplicación.|  
|BREAKRESUMEACTION\_CONTINUE|Sigue ejecutándose.|  
|BREAKRESUMEACTION\_STEP\_INTO|Pasos en un procedimiento.|  
|BREAKRESUMEACTION\_STEP\_OVER|Pasos más allá de un procedimiento.|  
|BREAKRESUMEACTION\_STEP\_OUT|Sale del procedimiento actual.|  
|BREAKRESUMEACTION\_IGNORE|Sigue ejecutándose con estado.|  
|BREAKRESUMEACTION\_STEP\_DOCUMENT|Pasos al siguiente documento.|  
  
## Vea también  
 [Active Script Debugger \(Constantes, enumeraciones y estructuras\)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)