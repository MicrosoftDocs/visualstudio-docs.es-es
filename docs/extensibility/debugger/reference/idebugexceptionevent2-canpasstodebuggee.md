---
title: IDebugExceptionEvent2::CanPassToDebuggee ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab57f599214cfbd7a1f5fcca15fa104b072d1d48
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729871"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Determina si el motor de depuración (DE) admite la opción de pasar esta excepción al programa que se está depurando cuando se reanuda la ejecución.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>Valor devuelto
 Devuelve `S_OK` (la excepción se puede pasar `S_FALSE` al programa) o (la excepción no se puede pasar).

## <a name="remarks"></a>Observaciones
 El DE debe tener una acción predeterminada para pasar al depurador. El IDE puede recibir el [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) eventos y `CanPassToDebuggee` llamar a la [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) método sin llamar al método. Por lo tanto, el DE debe tener un caso predeterminado para pasar la excepción en o no.

## <a name="see-also"></a>Vea también
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [Continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
