---
title: "Función JsGetPropertyIdFromName | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsGetPropertyIdFromName
helpviewer_keywords: JsGetPropertyIdFromName function
ms.assetid: 1674906f-746a-4c62-99cd-023276683a86
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c8779999bf2d03ce1a7435ad55848b5acbdc601
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jsgetpropertyidfromname-function"></a>JsGetPropertyIdFromName (Función)
Obtiene el identificador de propiedad asociado al nombre.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsGetPropertyIdFromName(  
   _In_z_ const wchar_t *name,  
   _Out_ JsPropertyIdRef *propertyId  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `name`  
 El nombre del identificador de propiedad que se va a obtener o crear. El nombre puede estar formado solo por dígitos.  
  
 `propertyId`  
 El identificador de propiedad de este runtime para el nombre especificado.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Los identificadores de propiedad son específicos de un contexto y no se pueden usar en todos los contextos.  
  
 Requiere un contexto de script activo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)