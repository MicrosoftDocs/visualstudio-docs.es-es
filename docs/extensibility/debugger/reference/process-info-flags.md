---
title: PROCESS_INFO_FLAGS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 36c4cbbe17a109eacd69b76500e8c10d21d2d554
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713966"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS

Describe o especifica las propiedades de un proceso.

## <a name="syntax"></a>Sintaxis

```cpp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
typedef DWORD PROCESS_INFO_FLAGS;
```

```csharp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
```

## <a name="fields"></a>Fields

`PIFLAG_SYSTEM_PROCESS`\
Indica que el proceso es un proceso del sistema.

`PIFLAG_DEBUGGER_ATTACHED`\
Indica que un depurador está depurando el proceso. Puede ser [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] un depurador, o puede ser algún otro depurador, por ejemplo, WinDbg.

`PIFLAG_PROCESS_STOPPED`\
Indica que el proceso está detenido. Válido solo `PIFLAG_DEBUGGER_ATTACHED` si también se especifica. Disponible en Visual Studio 2005 y versiones posteriores.

`PIFLAG_PROCESS_RUNNING`\
Indica que el proceso se está ejecutando. Válido solo `PIFLAG_DEBUGGER_ATTACHED` si también se especifica. Disponible en Visual Studio 2005 y versiones posteriores.

## <a name="remarks"></a>Observaciones

Se utiliza `Flags` para el miembro de la estructura [PROCESS_INFO.](../../../extensibility/debugger/reference/process-info.md)

Estas banderas se pueden `OR`combinar con un bit a bit .

## <a name="requirements"></a>Requisitos

Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también

- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
