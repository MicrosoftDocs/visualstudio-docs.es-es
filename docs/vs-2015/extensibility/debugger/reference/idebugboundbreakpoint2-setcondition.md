---
title: 'IDebugBoundBreakpoint2:: SetCondition | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugBoundBreakpoint2::SetCondition method
ms.assetid: 5d366876-efed-43d0-8ea1-dfdb009cbfac
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8ac19bfe2109d7885265342ccc5ef4d358727d49
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156207"
---
# <a name="idebugboundbreakpoint2setcondition"></a>IDebugBoundBreakpoint2::SetCondition
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Establece o cambia la condición asociada a este punto de interrupción enlazado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
```csharp  
int SetCondition(   
   enum_BP_CONDITION bpCondition  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `bpCondition`  
 de Un valor de la enumeración [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) que describe la condición.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Devuelve `E_BP_DELETED` si el estado del objeto de punto de interrupción enlazado se establece en `BPS_DELETED` (parte de la enumeración [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) ).  
  
## <a name="remarks"></a>Comentarios  
 Se pierde cualquier condición que se asoció previamente a este punto de interrupción.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
