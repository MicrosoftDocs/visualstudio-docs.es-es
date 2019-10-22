---
title: Enumeración PROFILER_EVENT_MASK | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: c1e1e7f3b604832014cb23245b105756d1126c5b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572281"
---
# <a name="profiler_event_mask-enumeration"></a>PROFILER_EVENT_MASK (Enumeración)
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
|PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL|Perfiles funciones que se definen en el código dinámico y el script escrito por el usuario.|  
|PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL|Genera perfiles de funciones nativas definidas por el motor de scripting.|  
|PROFILER_EVENT_MASK_TRACE_ALL|Genera perfiles de todas las funciones definidas por el usuario y del motor de scripting, excluidas las llamadas en el Document Object Model (DOM).|  
|PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL|Perfiles funciones que llaman a DOM.|  
|PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM|Genera perfiles de todas las funciones, incluidas las llamadas a DOM.|  
  
## <a name="see-also"></a>Vea también  
 [Active script Profiler (constantes, enumeraciones y estructuras)](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)    
 [Iactivescriptprofilercontrol (:: SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)    
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)