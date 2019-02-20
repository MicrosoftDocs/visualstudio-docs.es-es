---
title: BP_RES_DATA_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_RES_DATA_FLAGS
helpviewer_keywords:
- BP_RES_DATA_FLAGS enumeration
ms.assetid: d97611e2-def6-45a9-ad7d-eedf2ad4c82b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b111e98edb1d364a466157a6db4c0089617f18de
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "56413025"
---
# <a name="bpresdataflags"></a>BP_RES_DATA_FLAGS
Especifica si se está emulando el punto de interrupción de datos o implementadas en hardware.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_BP_RES_DATA_FLAGS {
    BP_RES_DATA_EMULATED = 0x0001
};
typedef DWORD BP_RES_DATA_FLAGS;
```

```csharp
public enum enum_BP_RES_DATA_FLAGS {
    BP_RES_DATA_EMULATED = 0x0001
};
```

## <a name="members"></a>Miembros
BP_RES_DATA_EMULATED  
Especifica que se está emulando el punto de interrupción de datos.

## <a name="remarks"></a>Comentarios
Utilizado para la `dwFlags` miembro de la [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) estructura.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
[Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
