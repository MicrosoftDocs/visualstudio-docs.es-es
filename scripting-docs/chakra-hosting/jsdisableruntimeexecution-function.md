---
title: "Función JsDisableRuntimeExecution | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsDisableRuntimeExecution
helpviewer_keywords: JsDisableRuntimeExecution function
ms.assetid: 4bd4670a-a9da-4f8c-b3fd-1fd366d915c3
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f44545f7c81344a2d22f0083087f77ac8074278c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jsdisableruntimeexecution-function"></a>JsDisableRuntimeExecution (Función)
Suspende la ejecución de scripts y termina los scripts en ejecución en un runtime.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsDisableRuntimeExecution(  
   _In_ JsRuntimeHandle runtime  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `runtime`  
 El runtime que se va a suspender.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Las llamadas a un runtime suspendido producirán errores hasta que se llame a `JsEnableRuntimeExecution`.  
  
 No se debe llamar a esta API en el subproceso en el que está activo el runtime. Aunque el runtime se colocará en un estado suspendido, es posible que un script en ejecución no se pueda suspender inmediatamente; este script terminará tan pronto como sea posible con una excepción que no se puede detectar.  
  
 La suspensión de la ejecución en un runtime que ya está suspendido es una operación inefectiva.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)