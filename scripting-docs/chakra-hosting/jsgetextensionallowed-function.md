---
title: Función JsGetExtensionAllowed | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsGetExtensionAllowed
helpviewer_keywords:
- JsGetExtensionAllowed function
ms.assetid: 839054a1-d643-47d9-89db-6a015bba0d91
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a515a0cc87eb8ab7f72a9f9fc02d4270abfa1484
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568055"
---
# <a name="jsgetextensionallowed-function"></a>JsGetExtensionAllowed (Función)
Devuelve un valor que indica si un objeto es extensible o no.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsGetExtensionAllowed(  
   _In_ JsValueRef object,  
   _Out_ bool *value  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `object`  
 El objeto que se va a probar.  
  
 `value`  
 Indica si el objeto es extensible o no.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Requiere un contexto de script activo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)