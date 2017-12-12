---
title: "Función JsGetAndClearException | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsGetAndClearException
helpviewer_keywords: JsGetAndClearException function
ms.assetid: 6aec8a88-41ee-47f6-b5f4-32f3cae6bb7b
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3e7e4f89bac59aa776762586ab20fa831b5c24bf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jsgetandclearexception-function"></a>JsGetAndClearException (Función)
Devuelve la excepción que hizo que el runtime del contexto actual se encuentre en el estado de excepción y restablece el estado de excepción para dicho runtime.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsGetAndClearException(  
   _Out_ JsValueRef *exception  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `exception`  
 La excepción para el runtime del contexto actual.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Si el runtime del contexto actual no está en un estado de excepción, esta API devolverá `JsErrorInvalidArgument`. Si el runtime está deshabilitado, esto devolverá una excepción que indica que el script terminó, pero no borrará la excepción (esta se borrará si se vuelve a habilitar el runtime mediante `JsEnableRuntimeExecution`).  
  
 Requiere un contexto de script activo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)