---
title: "Función JsIsRuntimeExecutionDisabled | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsIsRuntimeExecutionDisabled
helpviewer_keywords: JsIsRuntimeExecutionDisabled function
ms.assetid: 77490280-fb84-4614-a1f0-6ac31e3bd607
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4827205a33d337445faf9b0e9812133f0de3e97
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jsisruntimeexecutiondisabled-function"></a>JsIsRuntimeExecutionDisabled (Función)
Devuelve un valor que indica si la ejecución del script está deshabilitada en el runtime.  
  
## <a name="syntax"></a>Sintaxis  
  
```vb  
STDAPI_(JsErrorCode) JsIsRuntimeExecutionDisabled(    _In_ JsRuntimeHandle runtime,    _Out_ bool *isDisabled);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `runtime`  
 Especifica el runtime que se debe comprobar si la ejecución está deshabilitada.  
  
 `isDisabled`  
 Es `true` si la ejecución está deshabilitada; en caso contrario, es `false`.  
  
## <a name="return-value"></a>Valor devuelto  
 `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)