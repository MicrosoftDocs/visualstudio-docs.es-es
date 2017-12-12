---
title: "Función JsGetGlobalObject | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsGetGlobalObject
helpviewer_keywords: JsGetGlobalObject function
ms.assetid: d3e91e64-1ca3-4d2b-aada-725ded0fd0b1
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10ee0277098e29abd44c360be4dcd5b246c1b04d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jsgetglobalobject-function"></a>JsGetGlobalObject (Función)
Obtiene el objeto global del contexto de script actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsGetGlobalObject(  
   _Out_ JsValueRef *globalObject  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `globalObject`  
 El objeto global.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Requiere un contexto de script activo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)