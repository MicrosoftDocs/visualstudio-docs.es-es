---
title: DOCCONTEXT_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f31b33eeb782e71a87103d26a3bb78175611644e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318144"
---
# <a name="doccontextcompare"></a>DOCCONTEXT_COMPARE
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
Busque el primer contexto del documento en la lista que es igual que el contexto del documento de destino.

`DOCCONTEXT_LESS_THAN`\
Busque el primer contexto del documento en la lista que es menor que el contexto del documento de destino.

`DOCCONTEXT_GREATER_THAN`\
Busque el primer contexto del documento en la lista que es mayor que el contexto del documento de destino.

`DOCCONTEXT_SAME_DOCUMENT`\
Busque el primer contexto del documento en la lista que se encuentra en el mismo documento que el contexto del documento de destino.

## <a name="remarks"></a>Comentarios
Se pasa como argumento a la [comparar](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) método.

Estos valores se utilizan para especificar un criterio de comparación para encontrar el primer contexto del documento en una lista. Un contexto de documento se proporciona una lista de contextos de documento para comparar propio frente a través de la `IDebugDocumentContext2::Compare` método. El primer contexto de documento en la lista para que el operador de comparación es `true` , a continuación, se devuelve.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
