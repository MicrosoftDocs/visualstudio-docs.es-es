---
title: "Función JsHasException | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsHasException
helpviewer_keywords:
- JsHasException function
ms.assetid: ac7da3ce-c746-4154-bbb8-bcb0859a8d5b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 32334f4b8787bebaffb9553fcdd40f85334462cb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jshasexception-function"></a>JsHasException (Función)
Determina si el runtime del contexto actual está en un estado de excepción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsHasException(  
   _Out_ bool *hasException  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `hasException`  
 Indica si el runtime del contexto actual está en el estado de excepción.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Si una llamada al runtime produce una excepción (como resultado de ejecutar un script u otra circunstancia, como un error de conversión), el runtime se coloca en un "estado de excepción". Las llamadas realizadas en cualquier contexto de los creados por el runtime (salvo las API de excepción) producirán un error `JsErrorInExceptionState` hasta que se borre la excepción.  
  
 Si el runtime del contexto actual está en el estado de la excepción cuando una devolución de llamada vuelve al motor, este automáticamente volverá a producir la excepción.  
  
 Requiere un contexto de script activo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)