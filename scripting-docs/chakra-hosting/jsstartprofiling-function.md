---
title: "Función JsStartProfiling | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsStartProfiling
helpviewer_keywords: JsStartProfiling function
ms.assetid: 638da395-42dd-4fc5-b581-819e647e887d
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 964e9f26de9cb5000884089da0b404b8d22fdd8d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jsstartprofiling-function"></a>JsStartProfiling (Función)
Inicia la generación de perfiles en el contexto actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsStartProfiling(  
   _In_ IActiveScriptProfilerCallback *callback,  
   _In_ PROFILER_EVENT_MASK eventMask,  
   _In_ unsigned long context  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `callback`  
 La devolución de llamada de generación de perfiles que se va a usar.  
  
 `eventMask`  
 Los eventos de generación de perfiles con los que se va a realizar la devolución de llamada.  
  
 `context`  
 Contexto que se va a pasar a la devolución de llamada de generación de perfiles.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Requiere un contexto de script activo.  
  
 Esta API es compatible con aplicaciones de escritorio, pero no con aplicaciones de la Tienda.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)