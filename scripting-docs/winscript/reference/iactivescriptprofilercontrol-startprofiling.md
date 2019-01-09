---
title: IActiveScriptProfilerControl::StartProfiling | Microsoft Docs
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
ms.openlocfilehash: 3a64bbb790933513d29ee1a534472ac92c2072cf
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088301"
---
# <a name="iactivescriptprofilercontrolstartprofiling"></a>IActiveScriptProfilerControl::StartProfiling
Inicia la generación de perfiles en el motor de scripting. El motor de scripting crea una instancia del objeto del generador de perfiles mediante una llamada a [CoCreateInstance](https://docs.microsoft.com/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT StartProfiling(  
    [in] REFCLSID clsidProfilerObject,  
    [in] DWORD dwEventMask,  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `clsidProfilerObject`  
 [in] Identificador de clase (CLSID) del objeto del generador de perfiles que se va a crearse.  
  
 `dwEventMask`  
 [in] Una máscara de bits de 4 bytes que especifica los tipos de eventos. Los bits se definen en [PROFILER_EVENT_MASK (enumeración)](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
 `dwContext`  
 [in] Un valor de 4 bytes que se pasa al objeto del generador de perfiles.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un valor HRESULT. Los valores posibles son los siguientes:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|El método se realizó correctamente.|  
|`ACTIVPROF_E_PROFILER_PRESENT`|Ya está habilitada la generación de perfiles.|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptProfilerControl (Interfaz)](../../winscript/reference/iactivescriptprofilercontrol-interface.md)