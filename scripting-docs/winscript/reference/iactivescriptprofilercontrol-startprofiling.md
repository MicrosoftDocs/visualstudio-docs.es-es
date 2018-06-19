---
title: IActiveScriptProfilerControl::StartProfiling | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.StartProfiling
apilocation:
- scrobj.dll
ms.assetid: 56a7b3b7-8c21-43d0-9d8b-53bbc19fabb9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5362eaba439ff7a645a8323c4eed5d9496f6d88
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724875"
---
# <a name="iactivescriptprofilercontrolstartprofiling"></a>IActiveScriptProfilerControl::StartProfiling
Inicia la generación de perfiles en el motor de scripting. El motor de scripting crea una instancia del objeto de generador de perfiles mediante la realización de una llamada a [CoCreateInstance](http://msdn.microsoft.com/en-us/7295a55b-12c7-4ed0-a7a4-9ecee16afdec).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT StartProfiling(  
    [in] REFCLSID clsidProfilerObject,  
    [in] DWORD dwEventMask,  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `clsidProfilerObject`  
 [in] Identificador de clase (CLSID) del que se cree el objeto de generador de perfiles.  
  
 `dwEventMask`  
 [in] Una máscara de bits de 4 bytes que especifica los tipos de eventos. Los bits se definen en [PROFILER_EVENT_MASK (enumeración)](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
 `dwContext`  
 [in] Un valor de 4 bytes que se pasa al objeto de generador de perfiles.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un valor HRESULT. Los valores posibles son los siguientes:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|El método se realizó correctamente.|  
|`ACTIVPROF_E_PROFILER_PRESENT`|Ya está habilitada la generación de perfiles.|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptProfilerControl (Interfaz)](../../winscript/reference/iactivescriptprofilercontrol-interface.md)