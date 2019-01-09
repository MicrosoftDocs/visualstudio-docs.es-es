---
title: IActiveScriptProfilerControl2::CompleteProfilerStart | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::CompleteProfilerStart
ms.assetid: e14d94a2-39d3-40a1-84d9-6300fbe2b339
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b307352a3ba6d10ec3ae434536dee82d22504d33
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091291"
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
Notifica al generador de perfiles que ha iniciado la generación de perfiles en todos los motores de secuencias de comandos aplicables. Con este método, se puede obtener la pila de llamadas completa si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se ejecuta al iniciar la generación de perfiles.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT CompleteProfilerStart();  
```  
  
#### <a name="parameters"></a>Parámetros  
 El método no toma ningún parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un valor HRESULT. Los valores posibles son los siguientes:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_FAIL`|No se puede iniciar la generación de perfiles.|  
|`S_FALSE`|Se inició la generación de perfiles cuando no se está ejecutando una secuencia de comandos.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|No está habilitada la generación de perfiles. No se ha establecido ninguna devolución de llamada.|  
|`E_OUTOFMEMORY`|No se puede obtener la pila de llamadas debido a una condición de memoria insuficiente.|  
  
## <a name="remarks"></a>Comentarios  
 Una llamada a `IActiveScriptProfilerControl2::CompleteProfilerStart` garantiza que se envían los eventos para las funciones ya está en la pila de llamadas. Este método debe llamarse después de la generación de perfiles se inicia en cualquier motor de scripting que se encuentra en la ficha actual. El método se puede llamar para cualquier motor de scripting.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [IActiveScriptProfilerControl2 (Interfaz)](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)