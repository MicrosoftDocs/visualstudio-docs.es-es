---
title: Función JsGetNullValue | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsGetNullValue
helpviewer_keywords:
- JsGetNullValue function
ms.assetid: 132a1496-8dfe-4d3c-a8f8-389f5b0b50d2
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d4705f8cbf026002445693907ff70ab03030694
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24567975"
---
# <a name="jsgetnullvalue-function"></a>JsGetNullValue (Función)
Obtiene el valor de `null` en el contexto de script actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsGetNullValue(  
   _Out_ JsValueRef *nullValue  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `nullValue`  
 Valor de `null`.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Requiere un contexto de script activo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)