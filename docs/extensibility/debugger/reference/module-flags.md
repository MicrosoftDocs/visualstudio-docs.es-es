---
title: MODULE_FLAGS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 78c7f24d64ffca667706c3b2fcebeffad16a9d85
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714254"
---
# <a name="module_flags"></a>MODULE_FLAGS
Se utiliza para describir un módulo.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_MODULE_FLAGS { 
   MODULE_FLAG_NONE        = 0x0000,
   MODULE_FLAG_SYSTEM      = 0x0001,
   MODULE_FLAG_SYMBOLS     = 0x0002,
   MODULE_FLAG_64BIT       = 0x0004,
   MODULE_FLAG_OPTIMIZED   = 0x0008,
   MODULE_FLAG_UNOPTIMIZED = 0x0010
};
typedef DWORD MODULE_FLAGS;
```

```csharp
public enum enum_MODULE_FLAGS { 
   MODULE_FLAG_NONE        = 0x0000,
   MODULE_FLAG_SYSTEM      = 0x0001,
   MODULE_FLAG_SYMBOLS     = 0x0002,
   MODULE_FLAG_64BIT       = 0x0004,
   MODULE_FLAG_OPTIMIZED   = 0x0008,
   MODULE_FLAG_UNOPTIMIZED = 0x0010
};
```

## <a name="fields"></a>Fields
 `MODULE_FLAG_NONE`\
 No especifica ningún módulo.

 `MODULE_FLAG_SYSTEM`\
 Especifica un módulo del sistema.

 `MODULE_FLAG_SYMBOLS`\
 Especifica un módulo de símbolos.

 `MODULE_FLAG_64BIT`\
 Especifica un módulo de 64 bits.

 `MODULE_FLAG_OPTIMIZED`\
 Especifica que el módulo se ha optimizado. Este estado se refleja en la ventana **Módulos.**

 `MODULE_FLAG_UNOPTIMIZED`\
 Especifica que el módulo no se ha optimizado. Este estado se refleja en la ventana **Módulos.** Este es el estado predeterminado.

## <a name="remarks"></a>Observaciones
 Se utiliza `m_dwModuleFlags` para el miembro de la estructura [MODULE_INFO.](../../../extensibility/debugger/reference/module-info.md)

 Estas banderas se pueden `OR`combinar con un bit a bit .

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
