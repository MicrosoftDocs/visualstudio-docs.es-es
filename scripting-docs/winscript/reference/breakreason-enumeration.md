---
title: Enumeración BREAKREASON (| Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKREASON
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKREASON enumeration
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f656bdf4e3bc85a014ff8d3011708799aa44bcd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572628"
---
# <a name="breakreason-enumeration"></a>Enumeración BREAKREASON
Indica qué produjo la interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
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
  
## <a name="members"></a>Miembros  
  
|Miembro|Descripción|  
|------------|-----------------|  
|BREAKREASON_STEP|El motor de lenguaje está en modo de ejecución paso a paso.|  
|BREAKREASON_BREAKPOINT|El motor de lenguaje ha encontrado un punto de interrupción explícito.|  
|BREAKREASON_DEBUGGER_BLOCK|El motor de lenguaje encontró un bloque del depurador en otro subproceso.|  
|BREAKREASON_HOST_INITIATED|El host solicitó una interrupción.|  
|BREAKREASON_LANGUAGE_INITIATED|El motor de lenguaje solicitó una interrupción.|  
|BREAKREASON_DEBUGGER_HALT|El IDE del depurador solicitó una interrupción.|  
|BREAKREASON_ERROR|Un error de ejecución provocó la interrupción.|  
|BREAKREASON_JIT|Provocado por el inicio de la depuración JIT.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Debugger (Constantes, Enumeraciones y Estructuras)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)