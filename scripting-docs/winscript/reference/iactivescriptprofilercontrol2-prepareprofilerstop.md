---
title: Iactivescriptprofilercontrol2 (::P repareProfilerStop | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 24d4d73e0263882ad028ea66d3fac5e24f3af9ba
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571445"
---
# <a name="iactivescriptprofilercontrol2prepareprofilerstop"></a>IActiveScriptProfilerControl2::PrepareProfilerStop
Notifica al generador de perfiles que va a detener la generación de perfiles en todos los motores de scripts aplicables. Con este método, puede obtener la pila de llamadas completa si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se está ejecutando al detener la generación de perfiles.  
  
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
|`S_FALSE`|La generación de perfiles se detuvo cuando no se estaba ejecutando un script.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|La generación de perfiles no está habilitada.|  
  
## <a name="remarks"></a>Comentarios  
 La llamada a `IActiveScriptProfilerControl2::PrepareProfilerStop` garantiza que se envíen los eventos de las funciones de la pila de llamadas. Se debe llamar a este método antes de detener la generación de perfiles en cualquier motor de scripting que esté en la pestaña actual. Se puede llamar al método para cualquier motor de scripting.  
  
## <a name="see-also"></a>Vea también  
 [Iactivescriptprofilercontrol2 (:: CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)    
 [IActiveScriptProfilerControl2 (Interfaz)](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)