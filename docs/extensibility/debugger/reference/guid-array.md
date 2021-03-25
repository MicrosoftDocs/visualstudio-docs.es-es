---
description: Describe una matriz de identificadores únicos para los motores de depuración disponibles.
title: GUID_ARRAY | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GUID_ARRAY structure
ms.assetid: 9e12500c-2c1c-49b1-a0ba-e08366c97eb8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 504c917d9fb2b1e2cd15ac8154faf70eaf98beec
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054587"
---
# <a name="guid_array"></a>GUID_ARRAY
Describe una matriz de identificadores únicos para los motores de depuración disponibles.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct tagGUID_ARRAY
{
    DWORD dwCount;
    GUID *Members;
} GUID_ARRAY;
```

```csharp
public struct GUID_ARRAY
{
    public uint dwCount;
    public Guid Members;
}
```

## <a name="members"></a>Miembros
`dwCount`\
Número de identificadores únicos de la matriz.

`Members`\
Matriz que contiene identificadores únicos.

## <a name="remarks"></a>Observaciones
El método [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md) devuelve esta estructura.

## <a name="requirements"></a>Requisitos
Encabezado: Msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)
