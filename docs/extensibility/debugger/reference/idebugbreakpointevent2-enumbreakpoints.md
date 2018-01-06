---
title: IDebugBreakpointEvent2::EnumBreakpoints | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBreakpointEvent2:::EnumBreakpoints
helpviewer_keywords: IDebugBreakpointEvent2:::EnumBreakpoints
ms.assetid: 606a9625-ee43-4e84-9a47-af9a50d2d005
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 973c4442d42f6fe1b70be3515aba18f3f2424cb1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbreakpointevent2enumbreakpoints"></a>IDebugBreakpointEvent2::EnumBreakpoints
Crea un enumerador para todos los puntos de interrupción que ha activado en la ubicación actual del código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT EnumBreakpoints(  
  IEnumDebugBoundBreakpoints2** ppEnum  
);  
```  
  
```csharp  
int EnumBreakpoints(  
  out IEnumDebugBoundBreakpoints2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppEnum`  
 [out] Devuelve un [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) objeto que enumera todos los puntos de interrupción asociadas a la ubicación actual del código.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 No todos los puntos de interrupción en una ubicación concreta se pueden activar en un momento determinado (por ejemplo, un punto de interrupción con una condición no se activará hasta que se cumpla esa condición).  
  
## <a name="see-also"></a>Vea también  
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)