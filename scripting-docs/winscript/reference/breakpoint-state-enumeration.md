---
title: "BREAKPOINT_STATE (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: BREAKPOINT_STATE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "BREAKPOINT_STATE (enumeración)"
ms.assetid: 7adc9341-129a-4948-9669-0906d545fd5c
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# BREAKPOINT_STATE (Enumeraci&#243;n)
Indica el estado de un punto de interrupción.  
  
## Sintaxis  
  
```  
typedef enum tagBREAKPOINT_STATE {  
   BREAKPOINT_DELETED = 0,  
   BREAKPOINT_DISABLED = 1,  
   BREAKPOINT_ENABLED = 2  
} BREAKPOINT_STATE;  
```  
  
## Members  
  
|Miembro|Descripción|  
|-------------|-----------------|  
|BREAKPOINT\_DELETED|El punto de interrupción ya no existe, pero existen referencias a él.|  
|BREAKPOINT\_DISABLED|El punto de interrupción existe pero se deshabilita.|  
|BREAKPOINT\_ENABLED|El punto de interrupción existe y está habilitada.|  
  
## Vea también  
 [Active Script Debugger \(Constantes, enumeraciones y estructuras\)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)