---
title: "Función JsValueToVariant | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsValueToVariant
helpviewer_keywords: JsValueToVariant function
ms.assetid: 070244be-a69d-4b78-971b-69c0579c03cf
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2beb0a72a8e19d38d80ab8bf29ce0478ba7f481f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jsvaluetovariant-function"></a>JsValueToVariant (Función)
Inicializa la estructura `VARIANT` pasada como una proyección de un valor de JavaScript.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsValueToVariant(  
   _In_ JsValueRef object,  
   _Out_ VARIANT *variant  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `object`  
 Un valor de JavaScript que se va a proyectar como una estructura `VARIANT`.  
  
 `variant`  
 Un puntero a una estructura `VARIANT` que se inicializará como una proyección.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 La proyección `VARIANT` pueden usarla los clientes de automatización COM para llamar al objeto de JavaScript proyectado.  
  
 Requiere un contexto de script activo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)