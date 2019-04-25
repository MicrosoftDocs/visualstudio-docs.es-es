---
title: ATTACH_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11fba0944ca1b23c22caae6f0d6a4d9455099946
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56688269"
---
# <a name="attachreason"></a>ATTACH_REASON
Especifica la razón para el motor de depuración (DE) para asociar a un nodo de programa.

## <a name="syntax"></a>Sintaxis

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

## <a name="members"></a>Miembros
ATTACH_REASON_AUTO adjuntar porque el proceso está actualmente en modo de depuración.

ATTACH_REASON_LAUNCH adjuntar porque se ha iniciado el proceso.

Adjuntar ATTACH_REASON_USER debido a una solicitud de usuario.

## <a name="remarks"></a>Comentarios
Estos valores se usan como un parámetro a la [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md) y [adjuntar](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) métodos.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Asociar](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Asociar](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)
