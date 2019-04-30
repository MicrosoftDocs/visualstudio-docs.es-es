---
title: SCRIPTTHREADSTATE (enumeración) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADSTATE enum
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 906a309b25a1fe606fb37f8cbab70040e5a4c46f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840192"
---
# <a name="scriptthreadstate-enumeration"></a>SCRIPTTHREADSTATE (Enumeración)
Especifica el estado de un subproceso en un motor de scripting. Esta enumeración se utiliza en el [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md) método.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## <a name="enumeration-values"></a>Valores de enumeración  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE_NOTINSCRIPT|Subproceso especificado actualmente no es un evento con secuencias de comandos, el texto del script se ejecuta inmediatamente el procesamiento, de mantenimiento o ejecuta una macro de secuencia de comandos.|  
|SCRIPTTHREADSTATE_RUNNING|Subproceso especificado activamente el mantenimiento de un evento con secuencias de comandos, el texto del script se ejecuta inmediatamente el procesamiento, o ejecuta una macro de secuencia de comandos.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script (Constantes, Enumeraciones y Códigos de error)](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)