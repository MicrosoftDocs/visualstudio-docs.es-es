---
title: JsNativeFunction (Typedef) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 56ef6cdf-4ca9-4f7c-b953-e661addb1a8e
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33cf475dd6a17434ea132647b7d8bde833f0de9e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jsnativefunction-typedef"></a>JsNativeFunction (Typedef)
Una devolución de llamada de función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef _Ret_maybenull_ JsValueRef (CALLBACK * JsNativeFunction)(  
   _In_ JsValueRef callee,  
   _In_ bool isConstructCall,  
   _In_ JsValueRef *arguments,  
   _In_ unsigned short argumentCount  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 destinatario  
 Objeto `Function` que representa la función que se invoca.  
  
 isConstructCall  
 Indica si se trata de una llamada normal o una llamada “nueva”.  
  
 argumentos  
 Los argumentos de la llamada.  
  
 argumentCount  
 Número de argumentos.  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 El resultado de la llamada, si lo hay.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)