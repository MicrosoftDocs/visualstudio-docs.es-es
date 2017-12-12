---
title: "Función JsHasIndexedProperty | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsHasIndexedProperty
helpviewer_keywords: JsHasIndexedProperty function
ms.assetid: 30436a3d-fda0-407e-aba2-142be2310372
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 786be053ee501f60c633cd4b93f7b73acaa9b68d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jshasindexedproperty-function"></a>JsHasIndexedProperty (Función)
Prueba si un objeto tiene un valor en el índice especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsHasIndexedProperty(  
   _In_ JsValueRef object,  
   _In_ JsValueRef index,  
   _Out_ bool *result  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `object`  
 El objeto en el que se va a trabajar.  
  
 `index`  
 El índice que se va a probar.  
  
 `result`  
 Indica si el objeto tiene un valor en el índice especificado.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Requiere un contexto de script activo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)