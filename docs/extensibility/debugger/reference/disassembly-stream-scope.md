---
title: DISASSEMBLY_STREAM_SCOPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 724e32f83cfec31c2bacdab661407983af87efe6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318243"
---
# <a name="disassemblystreamscope"></a>DISASSEMBLY_STREAM_SCOPE
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

## <a name="fields"></a>Campos
`DSS_HUGE`\
Especifica que el desensamblado en el contexto del código generaría más resultados de un cliente normalmente desea recuperar en una sola llamada.

`DSS_FUNCTION`\
Especifica que se debe desensamblar la función contenida en el contexto del código. Especifica que la secuencia de desensamblado representa una función, cuando devuelve el [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) método.

`DSS_MODULE`\
Cuando devuelve el `IDebugDisassemblyStream2::GetScope` método, especifica que la secuencia de desensamblado representa un módulo.

`DSS_ALL`\
Especifica el desensamblado disponibles para el espacio de direcciones completa.

## <a name="remarks"></a>Comentarios
Pasa como argumento a la [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) método y devuelve el [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) método.

Estos valores se pueden combinar con un bit a bit `OR`.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)
