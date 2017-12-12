---
title: "Función JsBooleanToBool | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsBooleanToBool
helpviewer_keywords: JsBooleanToBool function
ms.assetid: ab16ac71-fe47-475d-a7ee-46e4643dee60
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f554d0a0d328254dde373e0b14c45e299a6df0a5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jsbooleantobool-function"></a>JsBooleanToBool (Función)
Recupera el valor `bool` de un valor booleano.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsBooleanToBool(  
   _In_ JsValueRef value,  
   _Out_ bool *boolValue  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `value`  
 El valor que se va a convertir.  
  
 `boolValue`  
 El valor convertido.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Requiere un contexto de script activo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)