---
title: Función JsSetProperty | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsSetProperty
helpviewer_keywords:
- JsSetProperty function
ms.assetid: 2c36bebf-ec86-425c-8131-2dd75fd30f40
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0930b0b3e59e2ea35f85295e2adc2cc5fdda33e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568695"
---
# <a name="jssetproperty-function"></a>JsSetProperty (Función)
Asigna un valor a una propiedad de un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsSetProperty(  
   _In_ JsValueRef object,  
   _In_ JsPropertyIdRef propertyId,  
   _In_ JsValueRef value,  
   _In_ bool useStrictRules  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `object`  
 El objeto que contiene la propiedad.  
  
 `propertyId`  
 El identificador de la propiedad.  
  
 `value`  
 Nuevo valor de la propiedad.  
  
 `useStrictRules`  
 La propiedad establecida debe seguir reglas de modo estrictas.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Requiere un contexto de script activo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)