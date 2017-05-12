---
title: "APPBREAKFLAGS (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: APPBREAKFLAGS
apilocation: scrobj.dll
helpviewer_keywords: 
  - "APPBREAKFLAGS (constantes)"
ms.assetid: ea8ed80f-2ddb-4800-bb3b-52b76ba6c7a0
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# APPBREAKFLAGS (Enumeraci&#243;n)
Indica el estado actual de la depuración de las aplicaciones y los subprocesos.  
  
## Sintaxis  
  
```cpp  
enum enum_APPBREAKFLAGS  
{  
APPBREAKFLAG_DEBUGGER_BLOCK= 0x00000001,  
APPBREAKFLAG_DEBUGGER_HALT= 0x00000002,  
APPBREAKFLAG_STEP= 0x00010000,  
APPBREAKFLAG_NESTED= 0x00020000,  
APPBREAKFLAG_STEPTYPE_SOURCE= 0x00000000,  
APPBREAKFLAG_STEPTYPE_BYTECODE= 0x00100000,  
APPBREAKFLAG_STEPTYPE_MACHINE= 0x00200000,  
APPBREAKFLAG_STEPTYPE_MASK= 0x00F00000,  
APPBREAKFLAG_IN_BREAKPOINT= 0x80000000  
};  
  
```  
  
## Members  
  
|Miembro|Valor|Descripción|  
|-------------|-----------|-----------------|  
|APPBREAKFLAG\_DEBUGGER\_BLOCK|0x00000001|El motor de lenguaje debe interrumpa inmediatamente en todos los subprocesos con BREAKREASON\_DEBUGGER\_BLOCK.|  
|APPBREAKFLAG\_DEBUGGER\_HALT|0x00000002|El motor de lenguaje debe interrumpa inmediatamente con BREAKREASON\_DEBUGGER\_HALT.|  
|APPBREAKFLAG\_STEP|0x00010000|El motor de lenguaje debe interrumpir inmediatamente en el subproceso de recorrido con BREAKREASON\_STEP.|  
|APPBREAKFLAG\_NESTED|0x00020000|La aplicación está en ejecución anidado en un punto de interrupción.|  
|APPBREAKFLAG\_STEPTYPE\_SOURCE|0x00000000|El depurador está recorriendo el nivel de origen.|  
|APPBREAKFLAG\_STEPTYPE\_BYTECODE|0x00100000|El depurador está recorriendo el nivel de código byte.|  
|APPBREAKFLAG\_STEPTYPE\_MACHINE|0x00200000|El depurador está recorriendo el nivel de equipo.|  
|APPBREAKFLAG\_STEPTYPE\_MASK|0x00F00000|Máscara para descomponer en factores out tipos de paso.|  
|APPBREAKFLAG\_IN\_BREAKPOINT|0x80000000|Un punto de interrupción está en curso.|  
  
## Comentarios  
 Algunos marcadores especifican que los motores de lenguajes deben interrumpir en la oportunidad siguiente, mientras que otros marcadores especifican el modo de entrada del depurador.  
  
## Vea también  
 [Active Script Debugger \(Constantes, enumeraciones y estructuras\)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)   
 [BREAKREASON \(Enumeración\)](../../winscript/reference/breakreason-enumeration.md)