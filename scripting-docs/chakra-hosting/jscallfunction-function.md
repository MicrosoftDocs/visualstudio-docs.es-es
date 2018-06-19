---
title: Función JsCallFunction | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsCallFunction
helpviewer_keywords:
- JsCallFunction function
ms.assetid: 8a1dca72-d720-4a28-a86e-6809465006fe
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb4ed76fbd387c16a78dae12c519e7a22c185243
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24567695"
---
# <a name="jscallfunction-function"></a>JsCallFunction (Función)
Invoca una función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsCallFunction(  
   _In_ JsValueRef function,  
   _In_reads_(argumentCount) JsValueRef *arguments,  
   _In_ unsigned short argumentCount,  
   _Out_opt_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `function`  
 La función que se va a invocar.  
  
 `arguments`  
 Los argumentos de la llamada.  
  
 `argumentCount`  
 El número de argumentos que se pasan a la función.  
  
 `result`  
 El valor devuelto por la invocación de la función, si existe.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Requiere un contexto de script activo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)