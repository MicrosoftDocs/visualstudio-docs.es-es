---
title: EncUnavailableReason | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 384d71d6f88e8cd792585bb097594fa7b1e38c64
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953752"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!` Representa las razones por las que **Editar y continuar** no está disponible.

## <a name="syntax"></a>Sintaxis

```cpp
enum tagEncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
typedef enum tagEncUnavailableReason EncUnavailableReason;
```

```csharp
public enum EncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
```

## <a name="fields"></a>Campos
`ENCUN_NONE`\
No hay ningún motivo específico por el que editar y continuar no esté disponible.

`ENCUN_INTEROP`\
Editar y continuar no está disponible durante una llamada de interoperabilidad.

`ENCUN_SQLCLR`\
Editar y continuar no está disponible durante una llamada a procedimiento SQL que usa Common Language Runtime (CLR).

`ENCUN_MINIDUMP`\
Editar y continuar no está disponible mientras se procesa un minivolcado.

`ENCUN_EMBEDDED`\
Editar y continuar no está disponible cuando se procesa código incrustado.

`ENCUN_ATTACH`\
La función editar y continuar no está disponible porque el depurador ha adjuntado la sesión, pero no la ha iniciado.

`ENCUN_WIN64`\
Editar y continuar no está disponible al procesar el código de Windows de 64 bits.

## <a name="remarks"></a>Notas
Esta enumeración solo es para uso interno por parte de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] . Los métodos [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) y [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) implementados por un proveedor de Puerto personalizado siempre deben devolver `E_NOTIMPL` .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. idl

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
