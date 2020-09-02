---
title: BP_LOCATION_DATA_STRING | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 82caf285d73ab1b9b49b9546012bbb45f25c3320
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153433"
---
# <a name="bp_location_data_string"></a>BP_LOCATION_DATA_STRING
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Se usa para establecer puntos de interrupción de datos que se basan en una cadena que el usuario puede especificar desde el entorno de desarrollo integrado (IDE).  
  
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
 El objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa el subproceso en el que se produce el punto de interrupción.  
  
 `bstrContext`  
 Contexto del punto de interrupción en el código, normalmente un nombre de método o función tal y como se ha detectado en una pila de llamadas.  
  
 `bstrDataExpr`  
 Cadena de datos que especifica el usuario para establecer el punto de interrupción.  
  
 `dwNumElements`  
 El número de elementos de la cadena de datos en los que se produce el punto de interrupción.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura es miembro de la estructura [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) como parte de una Unión.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
