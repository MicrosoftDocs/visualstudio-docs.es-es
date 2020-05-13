---
title: IDebugEngine2::RemoveAllSetExceptions ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords:
- IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ae5ac703f1d0bd374131a4f5de397f39cf0ba209
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731032"
---
# <a name="idebugengine2removeallsetexceptions"></a>IDebugEngine2::RemoveAllSetExceptions
Quita la lista de excepciones que el IDE ha establecido para una arquitectura o lenguaje en tiempo de ejecución determinado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT RemoveAllSetExceptions( 
   REFGUID guidType
);
```

```csharp
int RemoveAllSetExceptions( 
   ref Guid guidType
);
```

## <a name="parameters"></a>Parámetros
`guidType`\
[en] El GUID del lenguaje o el GUID del motor de depuración que es específico de una arquitectura en tiempo de ejecución.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Las excepciones quitadas por este método se establecieron mediante llamadas anteriores a la [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) método.

 Para quitar una excepción específica, llame a la [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) método.

## <a name="see-also"></a>Vea también
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
