---
title: IActiveScriptProfilerControl::SetProfilerEventMask | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.SetProfilerEventMask
apilocation:
- scrobj.dll
ms.assetid: 207e192f-e12e-4fcb-b4d8-eaee50ecb86e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 45ded6caec95f5421328be09e299af535765a9c2
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086793"
---
# <a name="iactivescriptprofilercontrolsetprofilereventmask"></a>IActiveScriptProfilerControl::SetProfilerEventMask
Establece una máscara de bits de 4 bytes que especifica los tipos de eventos que se debe generar el motor de scripting.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT SetProfilerEventMask(  
    [in] DWORD dwEventMask);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwEventMask`  
 [in] Una máscara de bits de 4 bytes que especifica los tipos de eventos. Los bits se definen en [PROFILER_EVENT_MASK (enumeración)](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un valor HRESULT. Los valores posibles son los siguientes:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|El método se realizó correctamente.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|No está habilitada la generación de perfiles.|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptProfilerControl (Interfaz)](../../winscript/reference/iactivescriptprofilercontrol-interface.md)