---
title: Función JsSetCurrentContext | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsSetCurrentContext
helpviewer_keywords:
- JsSetCurrentContext function
ms.assetid: 603cc94c-6585-411b-89f9-c6f144e2aa30
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd3daf7c97fa71ec19962233cdf5bd78bc4d2908
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568405"
---
# <a name="jssetcurrentcontext-function"></a>JsSetCurrentContext (Función)
Establece el contexto de script actual en el subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsSetCurrentContext(  
   _In_ JsContextRef context  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `context`  
 El contexto del script que se va a convertir en actual.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)