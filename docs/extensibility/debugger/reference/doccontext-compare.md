---
description: Especifica los criterios para comparar dos contextos de documento.
title: DOCCONTEXT_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6eeee3e31c898660930b676df716fe25769bbb8b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096010"
---
# <a name="doccontext_compare"></a>DOCCONTEXT_COMPARE
Especifica los criterios para comparar dos contextos de documento.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
typedef DWORD DOCCONTEXT_COMPARE;
```

```csharp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
```

## <a name="fields"></a>Campos
`DOCCONTEXT_EQUAL`\
Busque el primer contexto de documento en la lista que sea igual al contexto del documento de destino.

`DOCCONTEXT_LESS_THAN`\
Busque el primer contexto de documento en la lista que sea menor que el contexto del documento de destino.

`DOCCONTEXT_GREATER_THAN`\
Busque el primer contexto de documento en la lista que sea mayor que el contexto del documento de destino.

`DOCCONTEXT_SAME_DOCUMENT`\
Busque el primer contexto del documento en la lista que se encuentra en el mismo documento que el contexto del documento de destino.

## <a name="remarks"></a>Observaciones
Se pasa como argumento al método [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) .

Estos valores se usan para especificar un criterio de comparación para buscar el primer contexto de documento en una lista. A un contexto de documento se le asigna una lista de contextos de documento para compararlos a través del `IDebugDocumentContext2::Compare` método. A continuación, se devuelve el primer contexto del documento en la lista para el que se devuelve el operador de comparación `true` .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Comparar](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
