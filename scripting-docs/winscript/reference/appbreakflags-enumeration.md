---
title: APPBREAKFLAGS (enumeración) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- APPBREAKFLAGS
apilocation:
- scrobj.dll
helpviewer_keywords:
- APPBREAKFLAGS constants
ms.assetid: ea8ed80f-2ddb-4800-bb3b-52b76ba6c7a0
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0862e6fc670be6cd3d3ca9fbf67f453aa0772a90
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009777"
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
|APPBREAKFLAG_DEBUGGER_BLOCK|0x00000001|Motor de lenguaje se debe interrumpir inmediatamente en todos los subprocesos con BREAKREASON_DEBUGGER_BLOCK.|  
|APPBREAKFLAG_DEBUGGER_HALT|0x00000002|Motor de lenguaje se debe interrumpir inmediatamente con BREAKREASON_DEBUGGER_HALT.|  
|APPBREAKFLAG_STEP|0x00010000|Motor de lenguaje se debe interrumpir inmediatamente en el subproceso de ejecución paso a paso con BREAKREASON_STEP.|  
|APPBREAKFLAG_NESTED|0x00020000|La aplicación está en ejecución anidada en un punto de interrupción.|  
|APPBREAKFLAG_STEPTYPE_SOURCE|0x00000000|El depurador avanza un paso en el nivel de origen.|  
|APPBREAKFLAG_STEPTYPE_BYTECODE|0x00100000|El depurador avanza un paso en el nivel de código de bytes.|  
|APPBREAKFLAG_STEPTYPE_MACHINE|0x00200000|El depurador está aumentando el nivel de equipo.|  
|APPBREAKFLAG_STEPTYPE_MASK|0x00F00000|Máscara de factorización de los tipos de paso.|  
|APPBREAKFLAG_IN_BREAKPOINT|0x80000000|Un punto de interrupción está en curso.|  
  
## <a name="remarks"></a>Comentarios  
 Algunas marcas de especifican que los motores de lenguaje deberían interrumpir en la siguiente oportunidad, mientras que otras marcas de especifican el modo de ejecución paso a paso del depurador.  
  
## <a name="see-also"></a>Vea también  
 [Active Script Debugger (constantes), enumeraciones y estructuras](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)   
 [BREAKREASON (Enumeración)](../../winscript/reference/breakreason-enumeration.md)