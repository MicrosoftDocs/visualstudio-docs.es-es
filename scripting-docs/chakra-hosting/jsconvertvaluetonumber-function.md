---
title: Función JsConvertValueToNumber | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsConvertValueToNumber
helpviewer_keywords:
- JsConvertValueToNumber function
ms.assetid: c47b8653-0591-4863-b8b5-33187b315816
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db3ebb8b49f197232c5137bf42151491ebee35ec
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24567965"
---
# <a name="jsconvertvaluetonumber-function"></a>JsConvertValueToNumber (Función)
Convierte el valor en número mediante la semántica estándar de JavaScript.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsConvertValueToNumber(  
   _In_ JsValueRef value,  
   _Out_ JsValueRef *numberValue  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `value`  
 El valor que se va a convertir.  
  
 `numberValue`  
 El valor convertido.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Requiere un contexto de script activo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)