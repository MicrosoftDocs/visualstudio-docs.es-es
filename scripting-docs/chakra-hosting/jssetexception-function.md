---
title: Función JsSetException | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsSetException
helpviewer_keywords:
- JsSetException function
ms.assetid: c528793a-2e1b-4ee1-bd2e-e63fd547dc40
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5d8fce71f14dedea02e1809fb72281f575f60604
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568595"
---
# <a name="jssetexception-function"></a>JsSetException (Función)
Establece el runtime del contexto actual en un estado de excepción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsSetException(  
   _In_ JsValueRef exception  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `exception`  
 La excepción de JavaScript que se va a establecer en el runtime del contexto actual.  
  
## <a name="return-value"></a>Valor devuelto  
 `JsNoError` si el motor se estableció en un estado de excepción; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Si el runtime del contexto actual ya está en un estado de excepción, esta API devolverá `JsErrorInExceptionState`.  
  
 Requiere un contexto de script activo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)