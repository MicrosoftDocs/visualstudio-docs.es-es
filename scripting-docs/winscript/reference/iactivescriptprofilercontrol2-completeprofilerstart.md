---
title: 'Iactivescriptprofilercontrol2 (:: CompleteProfilerStart | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: f0230ecb480792b5b24b7375f5b95926735d0a61
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571558"
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
Notifica al generador de perfiles que ha iniciado la generación de perfiles en todos los motores de scripting aplicables. Con este método, puede obtener la pila de llamadas completa si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se está ejecutando al iniciar la generación de perfiles.  
  
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
|`S_FALSE`|La generación de perfiles se inició cuando no se estaba ejecutando un script.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|La generación de perfiles no está habilitada. No se ha establecido ninguna devolución de llamada.|  
|`E_OUTOFMEMORY`|No se puede obtener la pila de llamadas debido a una condición de memoria insuficiente.|  
  
## <a name="remarks"></a>Comentarios  
 La llamada a `IActiveScriptProfilerControl2::CompleteProfilerStart` garantiza que se envíen los eventos de las funciones que ya se encuentran en la pila de llamadas. Se debe llamar a este método después de que se inicie la generación de perfiles en cualquier motor de scripting que esté en la pestaña actual. Se puede llamar al método para cualquier motor de scripting.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [IActiveScriptProfilerControl2 (Interfaz)](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)