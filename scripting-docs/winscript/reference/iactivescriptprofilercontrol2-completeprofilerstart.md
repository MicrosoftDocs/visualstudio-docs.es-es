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
ms.openlocfilehash: 5abd4ee4237991714bfe3d8ba21b083f1a1920cd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724505"
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
Notifica al generador de perfiles que se ha iniciado en todos los motores de scripts aplicable de generación de perfiles. Con este método, se puede obtener la pila de llamadas completa si [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] se ejecuta al iniciar la generación de perfiles.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
|`S_FALSE`|Se inició la generación de perfiles cuando no se estaba ejecutando una secuencia de comandos.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|No está habilitada la generación de perfiles. No se ha establecido ninguna devolución de llamada.|  
|`E_OUTOFMEMORY`|No se puede obtener la pila de llamadas debido a una condición de memoria insuficiente.|  
  
## <a name="remarks"></a>Comentarios  
 Al llamar a `IActiveScriptProfilerControl2::CompleteProfilerStart` garantiza que se envían los eventos para las funciones que ya se encuentran en la pila de llamadas. Este método debe llamarse después de la generación de perfiles se inicia en un motor de scripting que se encuentra en la ficha actual. El método puede llamarse para cualquier motor de scripting.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [IActiveScriptProfilerControl2 (Interfaz)](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)