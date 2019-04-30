---
title: BREAKREASON (enumeración) | Documentos de Microsoft
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
ms.openlocfilehash: 939d9f36c9838f02e58bc433d1a7bb9bef43c28d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955413"
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
|BREAKREASON_STEP|El motor de lenguaje está en el modo de ejecución paso a paso.|  
|BREAKREASON_BREAKPOINT|El motor de lenguaje detectó un punto de interrupción explícito.|  
|BREAKREASON_DEBUGGER_BLOCK|El motor de lenguaje detectó un bloque de depurador en otro subproceso.|  
|BREAKREASON_HOST_INITIATED|El host solicita un salto.|  
|BREAKREASON_LANGUAGE_INITIATED|El motor de lenguaje había solicitado un salto.|  
|BREAKREASON_DEBUGGER_HALT|El IDE del depurador solicita un salto.|  
|BREAKREASON_ERROR|Un error de ejecución había producido la interrupción.|  
|BREAKREASON_JIT|Causados por el inicio de depuración JIT.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Debugger (Constantes, Enumeraciones y Estructuras)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)