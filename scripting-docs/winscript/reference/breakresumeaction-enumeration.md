---
title: BREAKRESUMEACTION (enumeración) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 3186ac39353d11f327f7940ae5fc03ae2238ddd9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090473"
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