---
title: Enumeración APPBREAKFLAGS (| Microsoft Docs
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
ms.openlocfilehash: de6efbc20843fcaa73965334c18cf0e5c2a0abab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572663"
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
|APPBREAKFLAG_DEBUGGER_BLOCK|0x00000001|El motor de lenguaje debe interrumpirse inmediatamente en todos los subprocesos con BREAKREASON_DEBUGGER_BLOCK.|  
|APPBREAKFLAG_DEBUGGER_HALT|0x00000002|El motor de lenguaje debe interrumpirse inmediatamente con BREAKREASON_DEBUGGER_HALT.|  
|APPBREAKFLAG_STEP|0x00010000|El motor de lenguaje debe interrumpirse inmediatamente en el subproceso de ejecución con BREAKREASON_STEP.|  
|APPBREAKFLAG_NESTED|0x00020000|La aplicación está en ejecución anidada en un punto de interrupción.|  
|APPBREAKFLAG_STEPTYPE_SOURCE|0x00000000|El depurador se está ejecutando paso a paso en el nivel de origen.|  
|APPBREAKFLAG_STEPTYPE_BYTECODE|0x00100000|El depurador se está ejecutando paso a paso en el nivel de código de bytes.|  
|APPBREAKFLAG_STEPTYPE_MACHINE|0x00200000|El depurador se está ejecutando paso a paso en el nivel de equipo.|  
|APPBREAKFLAG_STEPTYPE_MASK|0x00F00000|Máscara para factorizar los tipos de paso.|  
|APPBREAKFLAG_IN_BREAKPOINT|0x80000000|Un punto de interrupción está en curso.|  
  
## <a name="remarks"></a>Comentarios  
 Algunas marcas especifican que los motores de idioma se deben interrumpir en la siguiente oportunidad, mientras que otros marcadores especifican el modo de ejecución del depurador.  
  
## <a name="see-also"></a>Vea también  
 [Constantes, enumeraciones y estructuras de Active script debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)   
 [BREAKREASON (Enumeración)](../../winscript/reference/breakreason-enumeration.md)