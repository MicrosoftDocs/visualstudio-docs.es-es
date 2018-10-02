---
title: BP_LOCATION_DATA_STRING | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c53fa0f14cbea9dc65fbc1f8c99680785066379a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581646"
---
# <a name="bplocationdatastring"></a>BP_LOCATION_DATA_STRING
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [BP_LOCATION_DATA_STRING](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/bp-location-data-string).  
  
Se usa para establecer puntos de interrupción de datos que se basan en una cadena que el usuario puede escribir en el entorno de desarrollo integrado (IDE).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
typedef struct _BP_LOCATION_DATA_STRING {   
   IDebugThread2* pThread;  
   BSTR           bstrContext;  
   BSTR           bstrDataExpr;  
   DWORD          dwNumElements;  
} BP_LOCATION_DATA_STRING;  
```  
  
## <a name="members"></a>Miembros  
 `pThread`  
 El [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa el subproceso en el que se produce el punto de interrupción.  
  
 `bstrContext`  
 El contexto del punto de interrupción dentro del código, que suele ser un nombre de método o una función como se muestra en una pila de llamadas.  
  
 `bstrDataExpr`  
 La cadena de datos que escribe el usuario para el punto de interrupción.  
  
 `dwNumElements`  
 El número de elementos en la cadena de datos en el que se produce el punto de interrupción.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura es un miembro de la [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) estructura como parte de una unión.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)

