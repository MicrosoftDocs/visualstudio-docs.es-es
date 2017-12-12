---
title: "Función JsAddRef | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsAddRef
helpviewer_keywords: JsAddRef function
ms.assetid: a7f3ed49-6a86-489a-abdf-c99428e79cae
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e55ab6643dd949b8b41962161f76648dba926e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jsaddref-function"></a>JsAddRef (Función)
Agrega una referencia a un objeto recolectado no utilizado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsAddRef(  
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
 Esta función solo debe llamarse en los identificadores `JsRef` que no se van a almacenar en alguna parte de la pila. La llamada a `JsAddRef` garantiza que el objeto al que `JsRef` hace referencia no se liberará hasta que se llame a `JsRelease`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)