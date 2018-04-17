---
title: IDebugErrorBreakpoint2::GetPendingBreakpoint | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugErrorBreakpoint2::GetPendingBreakpoint
helpviewer_keywords:
- IDebugErrorBreakpoint2::GetPendingBreakpoint
ms.assetid: 59d0defc-99fd-445c-bdac-8224d5dea3f9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a4bcd63435e380ea7d913bb984fe8cf464392d3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugerrorbreakpoint2getpendingbreakpoint"></a>IDebugErrorBreakpoint2::GetPendingBreakpoint
Obtiene el punto de interrupción pendiente que produjo el error.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetPendingBreakpoint (   
   IDebugPendingBreakpoint2** ppPendingBreakpoint  
);  
```  
  
```csharp  
int GetPendingBreakpoint (   
   out IDebugPendingBreakpoint2 ppPendingBreakpoint  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppPendingBreakpoint`  
 [out] Devuelve un [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) objeto que representa el punto de interrupción pendiente que no se pudo enlazar.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)