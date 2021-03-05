---
description: Determina si el motor de depuración (DE) admite o no la opción de pasar esta excepción al programa que se está depurando cuando se reanuda la ejecución.
title: 'IDebugExceptionEvent2:: CanPassToDebuggee | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b56996a5fa7cbf3c08842b783aa2d5dfc1131b8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152889"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Determina si el motor de depuración (DE) admite o no la opción de pasar esta excepción al programa que se está depurando cuando se reanuda la ejecución.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>Valor devuelto
 Devuelve `S_OK` (la excepción se puede pasar al programa) o `S_FALSE` (no se puede pasar la excepción).

## <a name="remarks"></a>Observaciones
 El DE debe tener una acción predeterminada para pasar al código depurado. El IDE puede recibir el evento [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) y llamar al método [continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) sin llamar al `CanPassToDebuggee` método. Por lo tanto, el valor DE debe tener un caso predeterminado para pasar la excepción en o no.

## <a name="see-also"></a>Consulte también
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [Continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
