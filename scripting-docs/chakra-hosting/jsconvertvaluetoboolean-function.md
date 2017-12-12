---
title: "Función JsConvertValueToBoolean | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsConvertValueToBoolean
helpviewer_keywords: JsConvertValueToBoolean function
ms.assetid: 7298ec72-a388-4334-b81b-1691ab4cecf0
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10e2a5c91fe255e3eb9f3689e07fcfa149eb0d22
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jsconvertvaluetoboolean-function"></a>JsConvertValueToBoolean (Función)
Convierte el valor a booleano mediante la semántica estándar de JavaScript.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsConvertValueToBoolean(  
   _In_ JsValueRef value,  
   _Out_ JsValueRef *booleanValue  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `value`  
 El valor que se va a convertir.  
  
 `booleanValue`  
 El valor convertido.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Requiere un contexto de script activo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)