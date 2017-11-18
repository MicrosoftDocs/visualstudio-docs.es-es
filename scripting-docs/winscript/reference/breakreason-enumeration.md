---
title: "Enumeración BREAKREASON | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: BREAKREASON
apilocation: scrobj.dll
helpviewer_keywords: BREAKREASON enumeration
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf1baa8b627df50db33cbd86302ce06e80c1cf34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="breakreason-enumeration"></a>Enumeración BREAKREASON
Indica qué produjo la interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
|BREAKREASON_BREAKPOINT|El motor del lenguaje encontró un punto de interrupción explícito.|  
|BREAKREASON_DEBUGGER_BLOCK|El motor de lenguaje detectó un bloque de depurador en otro subproceso.|  
|BREAKREASON_HOST_INITIATED|El host había solicitado un salto.|  
|BREAKREASON_LANGUAGE_INITIATED|El motor del lenguaje había solicitado un salto.|  
|BREAKREASON_DEBUGGER_HALT|Un salto había solicitada por el depurador IDE.|  
|BREAKREASON_ERROR|Un error de ejecución produjo la interrupción.|  
|BREAKREASON_JIT|Causados por el inicio de depuración JIT.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Debugger (Constantes, Enumeraciones y Estructuras)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)