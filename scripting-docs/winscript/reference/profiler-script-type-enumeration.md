---
title: PROFILER_SCRIPT_TYPE (enumeración) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_SCRIPT_TYPE
apilocation:
- scrobj.dll
ms.assetid: 3ab6633a-6241-44f0-b837-14336f70c71e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 279969ec0b50f705e39d2e29e700adc1e833ead3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734125"
---
# <a name="profilerscripttype-enumeration"></a>PROFILER_SCRIPT_TYPE (Enumeración)
Especifica el tipo de script.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef enum {  
    PROFILER_SCRIPT_TYPE_USER,  
    PROFILER_SCRIPT_TYPE_DYNAMIC,  
    PROFILER_SCRIPT_TYPE_NATIVE,  
    PROFILER_SCRIPT_TYPE_DOM  
} PROFILER_SCRIPT_TYPE;  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Descripción|  
|------------|-----------------|  
|PROFILER_SCRIPT_TYPE_USER|Especifica el código de la secuencia de comandos escritos por el usuario.|  
|PROFILER_SCRIPT_TYPE_DYNAMIC|Especifica el código de script que se genera dinámicamente durante la ejecución.|  
|PROFILER_SCRIPT_TYPE_NATIVE|Especifica el tipo de secuencia de comandos para las funciones nativas y objetos definidos por el motor de scripting.|  
|PROFILER_SCRIPT_TYPE_DOM|Especifica una llamada a Document Object Model (DOM) de Internet Explorer, por ejemplo, una llamada a la `document.getElementById` método.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Profiler constantes, enumeraciones y estructuras](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)