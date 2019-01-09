---
title: PROFILER_SCRIPT_TYPE (enumeración) | Microsoft Docs
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
ms.openlocfilehash: ac387af4601ff822982c10e61f9813b2db7e8047
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086915"
---
# <a name="profilerscripttype-enumeration"></a>PROFILER_SCRIPT_TYPE (Enumeración)
Especifica el tipo de script.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
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
|PROFILER_SCRIPT_TYPE_USER|Especifica el código de script escrito por el usuario.|  
|PROFILER_SCRIPT_TYPE_DYNAMIC|Especifica el código de script que se genera dinámicamente durante la ejecución.|  
|PROFILER_SCRIPT_TYPE_NATIVE|Especifica el tipo de secuencia de comandos para las funciones nativas y objetos definidos por el motor de scripting.|  
|PROFILER_SCRIPT_TYPE_DOM|Especifica una llamada a Document Object Model (DOM) de Internet Explorer, por ejemplo, una llamada a la `document.getElementById` método.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Profiler constantes, enumeraciones y estructuras](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)