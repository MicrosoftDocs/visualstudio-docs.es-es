---
title: IActiveScriptProfilerControl2::PrepareProfilerStop | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::PrepareProfilerStop
ms.assetid: e43a63bc-c44f-44a8-9db4-29062b9e6a16
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 086ec8b4a126c65162638afde4d8081269757e1c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089523"
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
Notifica al generador de perfiles que se va a detener la generación de perfiles en todos los motores de secuencias de comandos aplicables. Con este método, se puede obtener la pila de llamadas completa si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se está ejecutando cuando se detiene la generación de perfiles.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT PrepareProfilerStop();  
```  
  
#### <a name="parameters"></a>Parámetros  
 El método no toma ningún parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un valor HRESULT. Los valores posibles son los siguientes:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_FAIL`|No se pudo iniciar la generación de perfiles.|  
|`S_FALSE`|Se detuvo la generación de perfiles cuando no se está ejecutando una secuencia de comandos.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|No está habilitada la generación de perfiles.|  
  
## <a name="remarks"></a>Comentarios  
 Una llamada a `IActiveScriptProfilerControl2::PrepareProfilerStop` garantiza que se envían los eventos de funciones de la pila de llamadas. Este método debe llamarse antes de detener la generación de perfiles en cualquier motor de scripting que se encuentra en la ficha actual. El método se puede llamar para cualquier motor de scripting.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [IActiveScriptProfilerControl2 (Interfaz)](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)