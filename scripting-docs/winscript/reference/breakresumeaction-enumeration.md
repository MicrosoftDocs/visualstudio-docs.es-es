---
title: "Enumeración BREAKRESUMEACTION | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: BREAKRESUMEACTION
apilocation: scrobj.dll
helpviewer_keywords: BREAKRESUMEACTION enumeration
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1b830d314b1db40d7b83557d894ad6f8751bdf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="breakresumeaction-enumeration"></a>Enumeración BREAKRESUMEACTION
Describe cómo continuar desde un punto de interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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