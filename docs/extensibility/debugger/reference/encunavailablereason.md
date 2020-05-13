---
title: EncUnavailableReason ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28863549ab3eac96322530bc85c52697f20448c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737162"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!`Representa las razones por las que **Editar y continuar** no está disponible.

## <a name="syntax"></a>Sintaxis

```cpp
enum tagEncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
typedef enum tagEncUnavailableReason EncUnavailableReason;
```

```csharp
public enum EncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
```

## <a name="fields"></a>Fields
`ENCUN_NONE`\
No hay ninguna razón específica por la que Editar y continuar no esté disponible.

`ENCUN_INTEROP`\
Editar y continuar no está disponible durante una llamada InterOp.

`ENCUN_SQLCLR`\
Editar y continuar no está disponible durante una llamada a procedimiento SQL que usa Common Language Runtime (CLR).

`ENCUN_MINIDUMP`\
Editar y continuar no está disponible durante el procesamiento de un minivolcado.

`ENCUN_EMBEDDED`\
Editar y continuar no está disponible al procesar código incrustado.

`ENCUN_ATTACH`\
Editar y continuar no está disponible porque la sesión se adjuntó al depurador, no iniciado por el depurador.

`ENCUN_WIN64`\
Editar y continuar no está disponible al procesar código de Windows de 64 bits.

## <a name="remarks"></a>Observaciones
Esta enumeración es para [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]uso interno sólo por . Los [métodos GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) y [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) implementados por `E_NOTIMPL`un proveedor de puertos personalizado siempre deben devolver .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.idl

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
