---
title: "APPBREAKFLAGS (enumeración) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- APPBREAKFLAGS
apilocation:
- scrobj.dll
helpviewer_keywords:
- APPBREAKFLAGS constants
ms.assetid: ea8ed80f-2ddb-4800-bb3b-52b76ba6c7a0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 126dcd704a60b591b71913f2e8e739de35c14636
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="appbreakflags-enumeration"></a>APPBREAKFLAGS (Enumeración)
Indican el estado de depuración actual de aplicaciones y subprocesos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_APPBREAKFLAGS{APPBREAKFLAG_DEBUGGER_BLOCK= 0x00000001,APPBREAKFLAG_DEBUGGER_HALT= 0x00000002,APPBREAKFLAG_STEP= 0x00010000,APPBREAKFLAG_NESTED= 0x00020000,APPBREAKFLAG_STEPTYPE_SOURCE= 0x00000000,APPBREAKFLAG_STEPTYPE_BYTECODE= 0x00100000,APPBREAKFLAG_STEPTYPE_MACHINE= 0x00200000,APPBREAKFLAG_STEPTYPE_MASK= 0x00F00000,APPBREAKFLAG_IN_BREAKPOINT= 0x80000000};  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Valor|Descripción|  
|------------|-----------|-----------------|  
|APPBREAKFLAG_DEBUGGER_BLOCK|0x00000001|Motor del lenguaje se debería interrumpir inmediatamente en todos los subprocesos con BREAKREASON_DEBUGGER_BLOCK.|  
|APPBREAKFLAG_DEBUGGER_HALT|0x00000002|Motor de idioma se debe interrumpir inmediatamente con BREAKREASON_DEBUGGER_HALT.|  
|APPBREAKFLAG_STEP|0x00010000|Motor del lenguaje debe interrumpa inmediatamente en el subproceso de ejecución paso a paso con BREAKREASON_STEP.|  
|APPBREAKFLAG_NESTED|0x00020000|La aplicación está en ejecución anidada en un punto de interrupción.|  
|APPBREAKFLAG_STEPTYPE_SOURCE|0x00000000|El depurador es seguir los pasos en el nivel de origen.|  
|APPBREAKFLAG_STEPTYPE_BYTECODE|0 x 00100000|El depurador es seguir los pasos en el nivel de código de bytes.|  
|APPBREAKFLAG_STEPTYPE_MACHINE|0x00200000|El depurador es seguir los pasos en el nivel de equipo.|  
|APPBREAKFLAG_STEPTYPE_MASK|0x00F00000|Máscara de la factorización de los tipos de paso.|  
|APPBREAKFLAG_IN_BREAKPOINT|0x80000000|Un punto de interrupción está en curso.|  
  
## <a name="remarks"></a>Comentarios  
 Algunos marcadores para especifican que se deberían interrumpir motores de idioma en la siguiente oportunidad, mientras que otras marcas de especifican el modo de ejecución paso a paso del depurador.  
  
## <a name="see-also"></a>Vea también  
 [Active Script Debugger constantes, enumeraciones y estructuras](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)   
 [BREAKREASON (Enumeración)](../../winscript/reference/breakreason-enumeration.md)