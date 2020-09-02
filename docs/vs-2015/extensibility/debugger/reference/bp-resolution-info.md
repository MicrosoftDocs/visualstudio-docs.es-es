---
title: BP_RESOLUTION_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_INFO
helpviewer_keywords:
- BP_RESOLUTION_INFO structure
ms.assetid: ba0c162a-61e8-4a0b-811f-4c1d8a5d82f0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1ba3f95372774b811030244a20208edd6f226981
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153303"
---
# <a name="bp_resolution_info"></a>BP_RESOLUTION_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Describe la información de punto de interrupción enlazada para un punto de interrupción de código o un punto de interrupción de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
typedef struct _BP_RESOLUTION_INFO {   
   BPRESI_FIELDS          dwFields;  
   BP_RESOLUTION_LOCATION bpResLocation;  
   IDebugProgram2*        pProgram;  
   IDebugThread2*         pThread;  
} BP_RESOLUTION_INFO;  
```  
  
```csharp  
public struct BP_RESOLUTION_INFO {   
   public uint                   dwFields;  
   public BP_RESOLUTION_LOCATION bpResLocation;  
   public IDebugProgram2         pProgram;  
   public IDebugThread2          pThread;  
};  
```  
  
## <a name="members"></a>Miembros  
 `dwFields`  
 Colección de marcas de [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md) enumeraciones que especifica qué campos se rellenan.  
  
 `bpResLocation`  
 Estructura [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) que especifica la ubicación del punto de interrupción en el código o en los datos.  
  
 `pProgram`  
 El objeto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representa la aplicación en la que se produjo el error de punto de interrupción.  
  
 `pThread`  
 El objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa el subproceso en el que se está ejecutando la aplicación que contiene el error de punto de interrupción.  
  
## <a name="remarks"></a>Comentarios  
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)devuelve esta estructura.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)   
 [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
