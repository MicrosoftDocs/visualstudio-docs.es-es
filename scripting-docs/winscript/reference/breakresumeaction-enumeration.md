---
title: BREAKRESUMEACTION (enumeración) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKRESUMEACTION enumeration
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e5c79aacc64eb57282bf09f7e4673980396b37ea
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955294"
---
# <a name="breakresumeaction-enumeration"></a>Enumeración BREAKRESUMEACTION
Describe cómo continuar desde un punto de interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
typedef enum tagBREAKRESUME_ACTION {  
   BREAKRESUMEACTION_ABORT,  
   BREAKRESUMEACTION_CONTINUE,  
   BREAKRESUMEACTION_STEP_INTO,  
   BREAKRESUMEACTION_STEP_OVER,  
   BREAKRESUMEACTION_STEP_OUT,  
   BREAKRESUMEACTION_IGNORE,  
   BREAKRESUMEACTION_STEP_DOCUMENT,  
} BREAKRESUMEACTION;  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Descripción|  
|------------|-----------------|  
|BREAKRESUMEACTION_ABORT|Anula la aplicación.|  
|BREAKRESUMEACTION_CONTINUE|Sigue ejecutándose.|  
|BREAKRESUMEACTION_STEP_INTO|Pasos en un procedimiento.|  
|BREAKRESUMEACTION_STEP_OVER|Pasos más allá de un procedimiento.|  
|BREAKRESUMEACTION_STEP_OUT|Sale del procedimiento actual.|  
|BREAKRESUMEACTION_IGNORE|Sigue ejecutándose con estado.|  
|BREAKRESUMEACTION_STEP_DOCUMENT|Pasos al siguiente documento.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Debugger (Constantes, Enumeraciones y Estructuras)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)