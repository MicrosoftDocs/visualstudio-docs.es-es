---
title: 'Iactivescriptprofilercallback (:: Initialize | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.Initialize
apilocation:
- scrobj.dll
ms.assetid: a257111e-a50b-4962-9dd6-c893d40f6985
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bbbd61d6b3c10dcfffe2df215cc5a60d685dd803
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576441"
---
# <a name="iactivescriptprofilercallbackinitialize"></a>IActiveScriptProfilerCallback::Initialize
Se llama para inicializar el objeto de generador de perfiles cada vez que se inicia la generación de perfiles en un motor de scripting.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Initialize(  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwContext`  
 de Un valor de 4 bytes que se pasa a [iactivescriptprofilercontrol (:: perfiles](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md).  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un valor HRESULT. Los valores posibles son los siguientes:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Si el método no puede inicializar el objeto de generador de perfiles, debe devolver un error HRESULT para notificar al motor de scripting. En este caso, el motor de scripting debe llamar directamente a [iactivescriptprofilercallback (:: Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md), pasando el valor HRESULT en el parámetro y, a continuación, libera el objeto de generador de perfiles.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptProfilerCallback (Interfaz)](../../winscript/reference/iactivescriptprofilercallback-interface.md)