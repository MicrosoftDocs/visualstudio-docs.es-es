---
title: Función JsNumberToDouble | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsNumberToDouble
helpviewer_keywords:
- JsNumberToDouble function
ms.assetid: 5f52e8b6-2b70-49a3-879a-bd83ebf2ac33
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3dba3205bcb55d3a9a233a5125a4854210b20f5d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568785"
---
# <a name="jsnumbertodouble-function"></a>JsNumberToDouble (Función)
Recupera el valor `double` de un valor numérico.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsNumberToDouble(  
   _In_ JsValueRef value,  
   _Out_ double *doubleValue  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `value`  
 El valor numérico que se va a convertir en un valor `double`.  
  
 `doubleValue`  
 Valor de `double`.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Esta función recupera el valor de un valor numérico. Se producirá un error `JsErrorInvalidArgument` si el tipo del valor no es numérico.  
  
 Requiere un contexto de script activo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)