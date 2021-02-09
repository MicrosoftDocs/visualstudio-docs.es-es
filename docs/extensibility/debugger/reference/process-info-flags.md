---
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cd20b194623a02ff3852d0f0734f3dc7d7e1cfc6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923091"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS

Describe o especifica las propiedades de un proceso.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
typedef DWORD PROCESS_INFO_FLAGS;
```

```csharp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
```

## <a name="fields"></a>Campos

`PIFLAG_SYSTEM_PROCESS`\
Indica que el proceso es un proceso del sistema.

`PIFLAG_DEBUGGER_ATTACHED`\
Indica que un depurador está depurando el proceso. Puede ser un [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] depurador o puede ser algún otro depurador, por ejemplo, WinDbg.

`PIFLAG_PROCESS_STOPPED`\
Indica que el proceso está detenido. Solo es válido si `PIFLAG_DEBUGGER_ATTACHED` también se especifica. Disponible en Visual Studio 2005 y versiones posteriores.

`PIFLAG_PROCESS_RUNNING`\
Indica que el proceso se está ejecutando. Solo es válido si `PIFLAG_DEBUGGER_ATTACHED` también se especifica. Disponible en Visual Studio 2005 y versiones posteriores.

## <a name="remarks"></a>Notas

Se utiliza para el `Flags` miembro de la estructura [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) .

Estas marcas se pueden combinar con una operación bit a bit `OR` .

## <a name="requirements"></a>Requisitos

Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también

- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
