---
title: "SCRIPTTHREADSTATE (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: SCRIPTTHREADSTATE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SCRIPTTHREADSTATE (enum)"
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# SCRIPTTHREADSTATE (Enumeraci&#243;n)
Especifica el estado de un subproceso en un motor de script.  El método [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md) utiliza esta enumeración.  
  
## Sintaxis  
  
```  
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## Valores de enumeración  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE\_NOTINSCRIPT|El subproceso especificado no mantiene un evento con scripts, está procesando texto inmediatamente ejecutan del script, o no se está ejecutando actualmente una macro de script.|  
|SCRIPTTHREADSTATE\_RUNNING|El subproceso especificado mantiene un evento con scripts, está procesando texto inmediatamente ejecutan del script, o ejecutando activamente una macro de script.|  
  
## Vea también  
 [Active Script \(constantes, enumeraciones y códigos de error\)](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)