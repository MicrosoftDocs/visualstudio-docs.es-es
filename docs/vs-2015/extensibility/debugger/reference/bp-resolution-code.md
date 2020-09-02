---
title: BP_RESOLUTION_CODE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_CODE
helpviewer_keywords:
- BP_RESOLUTION_CODE structure
ms.assetid: ac103ec5-771c-4667-92de-b5abb53bbb52
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b2323ce082a41633afae33e90030b704f2e53f80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153325"
---
# <a name="bp_resolution_code"></a>BP_RESOLUTION_CODE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Describe la ubicación de un punto de interrupción de código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
typedef struct _BP_RESOLUTION_CODE {   
   IDebugCodeContext2* pCodeContext;  
} BP_RESOLUTION_CODE;  
```  
  
```csharp  
public struct BP_RESOLUTION_CODE {   
   public IDebugCodeContext2 pCodeContext;  
};  
```  
  
## <a name="members"></a>Miembros  
 `pCodeContext`  
 El objeto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) que identifica la posición del punto de interrupción en el código.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura es un miembro de la estructura [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) , que, a su vez, es miembro de la estructura [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) devuelta por el método [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) .  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
