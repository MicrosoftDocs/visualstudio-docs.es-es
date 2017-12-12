---
title: "Función JsRelease | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsRelease
helpviewer_keywords: JsRelease function
ms.assetid: 8714fd0b-5b66-48e0-927e-7b93af6cde7b
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd5dda0eaa8cd6767991eea3f2a1cf9c70c65a27
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jsrelease-function"></a>JsRelease (Función)
Libera una referencia a un objeto no utilizado recolectado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsRelease(  
   _In_ JsRef ref,  
   _Out_opt_ unsigned int *count  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ref`  
 El objeto al que se va a agregar una referencia.  
  
 `count`  
 El nuevo número de referencias del objeto (se puede pasar NULL).  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Quita una referencia a un identificador `JsRef` creado por `JsAddRef`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)