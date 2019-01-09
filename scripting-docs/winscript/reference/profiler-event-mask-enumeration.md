---
title: PROFILER_EVENT_MASK (enumeración) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_EVENT_MASK
apilocation:
- scrobj.dll
ms.assetid: c2168408-f4f6-4600-971d-f15b4edf4ca2
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da55371c24f6a21acbc9dc789a2c76ef6e7c66b4
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096673"
---
# <a name="profilereventmask-enumeration"></a>PROFILER_EVENT_MASK (Enumeración)
Indica los tipos de eventos de los que se deben generar perfiles.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
typedef enum {  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL = 0x00000001,  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL = 0x00000002,  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL    = 0x00000004,  
    PROFILER_EVENT_MASK_TRACE_ALL =  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL |  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL,  
    PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM = PROFILER_EVENT_MASK_TRACE_ALL |  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL  
} PROFILER_EVENT_MASK;  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Descripción|  
|------------|-----------------|  
|PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL|Funciones de perfiles que se definen en el script escrito por el usuario y código dinámico.|  
|PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL|Funciones nativas de los perfiles definidos por el motor de scripting.|  
|PROFILER_EVENT_MASK_TRACE_ALL|Los perfiles de todas las funciones del motor de scripting y definido por el usuario, las llamadas a Document Object Model (DOM).|  
|PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL|Funciones de perfiles que llaman a en el DOM.|  
|PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM|Los perfiles de todas las funciones, incluidas las llamadas en el DOM.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Profiler constantes, enumeraciones y estructuras](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)   
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)