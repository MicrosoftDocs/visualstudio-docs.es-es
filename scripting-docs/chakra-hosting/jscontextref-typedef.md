---
title: JsContextRef (Typedef) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8586bfcc-bb24-430d-a6f2-1a3b3e34ec2e
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec1300717b59c3b901665b39ca0102988e83e853
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jscontextref-typedef"></a>JsContextRef (Typedef)
Referencia a un contexto de script.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef JsRef JsContextRef;  
```  
  
## <a name="remarks"></a>Comentarios  
 Cada contexto de script incluye su propio objeto global, que es distinto del de otros contextos de script.  
  
 Muchas de las API de hospedaje de Chakra requieren un contexto de script "activo", que se puede establecer mediante `JsSetCurrentContext`. Las API de hospedaje de Chakra que requieran el establecimiento de un contexto actual lo indicarán explícitamente en la documentación.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)