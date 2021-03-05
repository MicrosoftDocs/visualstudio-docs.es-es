---
description: Especifica el motivo por el que el motor de depuración (DE) se debe adjuntar a un nodo de programa.
title: ATTACH_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f6fa83fb537f05a2c073e3693dab964fa58af464
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144616"
---
# <a name="attach_reason"></a>ATTACH_REASON
Especifica el motivo por el que el motor de depuración (DE) se debe adjuntar a un nodo de programa.

## <a name="syntax"></a>Syntax

```cpp
enum enum_ATTACH_REASON {
    ATTACH_REASON_LAUNCH = 0x0001,
    ATTACH_REASON_USER   = 0x0002,
    ATTACH_REASON_AUTO   = 0x0003
};
typedef DWORD ATTACH_REASON;
```

```csharp
public enum enum_ATTACH_REASON {
    ATTACH_REASON_LAUNCH = 0x0001,
    ATTACH_REASON_USER   = 0x0002,
    ATTACH_REASON_AUTO   = 0x0003
};
```

## <a name="fields"></a>Campos
`ATTACH_REASON_AUTO`\
Asociar porque el proceso está actualmente en modo de depuración.

`ATTACH_REASON_LAUNCH`\
Adjunte porque se ha iniciado el proceso.

`ATTACH_REASON_USER`\
Adjunte debido a una solicitud de usuario.

## <a name="remarks"></a>Observaciones
Estos valores se usan como parámetro para los métodos [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) y [Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Adjuntar](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)
