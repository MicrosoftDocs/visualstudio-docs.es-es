---
title: "Función JsGetOwnPropertyNames | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsGetOwnPropertyNames
helpviewer_keywords: JsGetOwnPropertyNames function
ms.assetid: 0c17ea06-b17f-4ea3-ad04-1259a4d1b6de
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4efd4133fb2636afdacba205f7be1ba7980a36c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jsgetownpropertynames-function"></a>JsGetOwnPropertyNames (Función)
Obtiene la lista de todas las propiedades del objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsGetOwnPropertyNames(  
   _In_ JsValueRef object,  
   _Out_ JsValueRef *propertyNames  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `object`  
 El objeto cutos nombres de propiedades se van a obtener.  
  
 `propertyNames`  
 Matriz de nombres de propiedades.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Requiere un contexto de script activo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)