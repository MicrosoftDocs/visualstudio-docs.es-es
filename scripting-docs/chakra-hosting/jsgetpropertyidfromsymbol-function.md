---
title: "Función JsGetPropertyIdFromSymbol | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 190fe4b9-352e-4b10-9d0e-6c6bbd6363e8
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab8150d9a56621366c75a50f004b26e1bc5d747b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jsgetpropertyidfromsymbol-function"></a>Función JsGetPropertyIdFromSymbol
Obtiene el identificador de propiedad asociado al símbolo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsGetPropertyIdFromSymbol(  
   _In_ JsValueRef symbol,  
   _Out_ JsPropertyIdRef *propertyId  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `symbol`  
 El símbolo cuyo identificador de propiedad se está recuperando.  
  
 `propertyId`  
 El identificador de propiedad para el símbolo dado.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Los identificadores de propiedad son específicos de un contexto y no se pueden usar en todos los contextos.  
  
 Requiere un contexto de script activo.  
  
 Esta API solo es compatible en modo perimetral.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)