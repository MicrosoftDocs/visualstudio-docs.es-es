---
title: Definición de tipo JsRef | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6aafc39f-6b9c-457f-8bf0-48831bffe9b8
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9d4c478a45f53e83dfa59fdde21cfa4c988c92e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568535"
---
# <a name="jsref-typedef"></a>JsRef (Typedef)
Referencia a un objeto propiedad del recolector de elementos no utilizados de Chakra.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef void *JsRef;  
```  
  
## <a name="remarks"></a>Comentarios  
 Un runtime de Chakra realizará automáticamente el seguimiento de las referencias a JsRef siempre que estas se almacenen en variables locales o en parámetros in (por ejemplo, en la pila). El almacenamiento de un JsRef en otro lugar que no sea la pila requiere llamar a JsAddRef y JsRelease para administrar la duración del objeto; de lo contrario, el recolector de elementos no utilizados puede liberar el objeto mientras está todavía en uso.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)