---
description: Quita la lista de excepciones que el IDE ha establecido para un idioma o una arquitectura en tiempo de ejecución determinados.
title: 'IDebugEngine2:: RemoveAllSetExceptions | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords:
- IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b40da7391fc360b68da70f02f4d32afb92e83a58
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087943"
---
# <a name="idebugengine2removeallsetexceptions"></a>IDebugEngine2::RemoveAllSetExceptions
Quita la lista de excepciones que el IDE ha establecido para un idioma o una arquitectura en tiempo de ejecución determinados.

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
de El GUID del lenguaje o el GUID del motor de depuración que es específico de una arquitectura en tiempo de ejecución.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Las excepciones quitadas por este método se establecieron mediante llamadas anteriores al método [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) .

 Para quitar una excepción concreta, llame al método [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) .

## <a name="see-also"></a>Consulte también
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
