---
title: CONTEXT_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f273bbab4a85f03a7da0d155d8b9e081693987c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912968"
---
# <a name="context_compare"></a>CONTEXT_COMPARE
Especifica los criterios para comparar dos contextos de memoria.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_CONTEXT_COMPARE {
    CONTEXT_EQUAL                 = 0x0001,
    CONTEXT_LESS_THAN             = 0x0002,
    CONTEXT_GREATER_THAN          = 0x0003,
    CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,
    CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,
    CONTEXT_SAME_SCOPE            = 0x0006,
    CONTEXT_SAME_FUNCTION         = 0x0007,
    CONTEXT_SAME_MODULE           = 0x0008,
    CONTEXT_SAME_PROCESS          = 0x0009
};
typedef DWORD CONTEXT_COMPARE;
```

```csharp
public enum enum_CONTEXT_COMPARE {
    CONTEXT_EQUAL                 = 0x0001,
    CONTEXT_LESS_THAN             = 0x0002,
    CONTEXT_GREATER_THAN          = 0x0003,
    CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,
    CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,
    CONTEXT_SAME_SCOPE            = 0x0006,
    CONTEXT_SAME_FUNCTION         = 0x0007,
    CONTEXT_SAME_MODULE           = 0x0008,
    CONTEXT_SAME_PROCESS          = 0x0009
};
```

## <a name="fields"></a>Campos
`CONTEXT_EQUAL`\
Busque el primer contexto de memoria de la lista que sea igual al contexto de memoria de destino.

`CONTEXT_LESS_THAN`\
Busque el primer contexto de memoria de la lista que sea menor que el contexto de memoria de destino.

`CONTEXT_GREATER_THAN`\
Busque el primer contexto de memoria de la lista que sea mayor que el contexto de memoria de destino.

`CONTEXT_LESS_THAN_OR_EQUAL`\
Busque el primer contexto de memoria de la lista que sea menor o igual que el contexto de memoria de destino.

`CONTEXT_GREATER_THAN_OR_EQUAL`\
Busque el primer contexto de memoria de la lista que sea mayor o igual que el contexto de memoria de destino.

`CONTEXT_SAME_SCOPE`\
Busque el primer contexto de memoria de la lista que está en el mismo ámbito que el contexto de memoria de destino.

`CONTEXT_SAME_FUNCTION`\
Busque el primer contexto de memoria de la lista que está en la misma función que el ámbito de la memoria de destino.

`CONTEXT_SAME_MODULE`\
Busque el primer contexto de memoria de la lista que se encuentra en el mismo módulo que el contexto de memoria de destino.

`CONTEXT_SAME_PROCESS`\
Busque el primer contexto de memoria de la lista que se encuentre en el mismo proceso que el contexto de memoria de destino.

## <a name="remarks"></a>Notas
Se pasa como argumento al método [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) .

Estos valores se utilizan para buscar el primer contexto de memoria de una lista que cumpla los criterios de comparación especificados. A un contexto de memoria se le asigna una lista de contextos de memoria que se van a comparar a través del `IDebugMemoryContext2::Compare` método. El primer contexto de memoria de la lista para la que se devuelve el operador de comparación `true` .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Comparar](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)
