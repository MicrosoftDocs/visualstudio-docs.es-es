---
title: "Definición de tipo JsRuntimeHandle | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 69e59bfd-9b0e-4710-9aa8-fbd6844171bc
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d3c0344e203c58691048c55ba4080c6c86c1c643
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jsruntimehandle-typedef"></a>JsRuntimeHandle (Typedef)
Identificador para un runtime de Chakra.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef void *JsRuntimeHandle;  
```  
  
## <a name="remarks"></a>Comentarios  
 Cada runtime de Chakra tiene su propio motor de ejecución, compilador JIT y montón de recolección de elementos no utilizados independientes. Como tal, cada runtime está completamente aislado del resto.  
  
 Los runtime se pueden usar en cualquier subproceso, pero solo un subproceso puede llamar a un runtime en un momento determinado.  
  
> [!WARNING]
>  Al contrario que otras referencias a objetos de la API de hospedaje de Chakra, los elementos no utilizados de un JsRuntimeHandle no se recolectan, puesto que este contiene el propio montón de recolección de elementos no utilizados. Un runtime seguirá existiendo hasta que se llame a JsDisposeRuntime.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)