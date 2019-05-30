---
title: IDebugPendingBreakpoint2::SetPassCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5af01702c20b4841c5d737bef2c3be7f885cc31e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340562"
---
# <a name="idebugpendingbreakpoint2setpasscount"></a>IDebugPendingBreakpoint2::SetPassCount
Establece o cambia el recuento de pass asociado con el punto de interrupción pendiente.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

```csharp
int SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

## <a name="parameters"></a>Parámetros
`bpPassCount`\
[in] Un [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) estructura que contiene el recuento de pass.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Devuelve `E_BP_DELETED` si se ha eliminado el punto de interrupción.

## <a name="remarks"></a>Comentarios
 Se pierde cualquier contador de pasos que asoció anteriormente con el punto de interrupción pendiente. Todos los puntos de interrupción enlazados desde este punto de interrupción pendiente de se llaman para establecer su recuento de paso en el `bpPassCount` parámetro.

## <a name="see-also"></a>Vea también
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)