---
title: EncUnavailableReason | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ccc05c58eafe6f8902b3f8ac09b90dc771a3009
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315695"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!` Representa los motivos que **editar y continuar** no está disponible.

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

#### <a name="parameters"></a>Parámetros
ENCUN_NONE  
No hay motivo específico por editar y continuar no está disponible.

ENCUN_INTEROP  
Editar y continuar no está disponible durante una llamada de interoperabilidad.

ENCUN_SQLCLR  
Editar y continuar no está disponible durante una llamada de procedimiento SQL que utiliza Common Language Runtime (CLR).

ENCUN_MINIDUMP  
Editar y continuar no está disponible mientras se procesaba un minivolcado.

ENCUN_EMBEDDED  
Editar y continuar no está disponible cuando se procesa código incrustado.

ENCUN_ATTACH  
Editar y continuar no está disponible porque se ha adjuntado a la sesión, no se inicia mediante el depurador.

ENCUN_WIN64  
Editar y continuar no está disponible durante el procesamiento de código de Windows de 64 bits.

## <a name="remarks"></a>Comentarios
Esta enumeración es para uso interno únicamente por [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]. El [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) y [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) siempre deben devolver métodos tal como está implementado por un proveedor de puerto personalizado `E_NOTIMPL`.

## <a name="requirements"></a>Requisitos
Header: msdbg.idl

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
[Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)

