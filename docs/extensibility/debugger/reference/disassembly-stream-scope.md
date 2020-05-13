---
title: DISASSEMBLY_STREAM_SCOPE Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fae1f22c6db22cd6cff93cfb1b98a28620a1537c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737272"
---
# <a name="disassembly_stream_scope"></a>DISASSEMBLY_STREAM_SCOPE
Especifica el ámbito de la secuencia de desensamblado.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
typedef DWORD DISASSEMBLY_STREAM_SCOPE;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
```

## <a name="fields"></a>Fields
`DSS_HUGE`\
Especifica que desensamblar el contexto de código generaría más resultados de los que un cliente normalmente desearía recuperar en una sola llamada.

`DSS_FUNCTION`\
Especifica que se debe desensamblar la función contenida en el contexto de código. Especifica que la secuencia de desensamblado representa una función, cuando se devuelve por el [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) método.

`DSS_MODULE`\
Cuando el `IDebugDisassemblyStream2::GetScope` método lo devuelve, especifica que la secuencia de desensamblado representa un módulo.

`DSS_ALL`\
Especifica el desensamblado para todo el espacio de direcciones.

## <a name="remarks"></a>Observaciones
Se pasa como argumento al método [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) y devuelto por el método [GetScope.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)

Estos valores se pueden combinar `OR`con un archivo .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)
