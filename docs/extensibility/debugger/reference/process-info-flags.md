---
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42a596eb8d720a273d89586427232dcf833f8595
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696524"
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS

Describen o especifican las propiedades de un proceso.

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

## <a name="members"></a>Miembros

PIFLAG_SYSTEM_PROCESS indica que el proceso es un proceso del sistema.

PIFLAG_DEBUGGER_ATTACHED indica que el proceso se está depurando un depurador. Puede ser un [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] depurador, o bien puede ser algún otro depurador, por ejemplo, WinDbg.

PIFLAG_PROCESS_STOPPED indica que el proceso se detiene. Sólo es válido si `PIFLAG_DEBUGGER_ATTACHED` también se especifica. Disponible en Visual Studio 2005 y versiones posteriores.

PIFLAG_PROCESS_RUNNING indica que el proceso se está ejecutando. Sólo es válido si `PIFLAG_DEBUGGER_ATTACHED` también se especifica. Disponible en Visual Studio 2005 y versiones posteriores.

## <a name="remarks"></a>Comentarios

Utilizado para la `Flags` miembro de la [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) estructura.

Estas marcas se pueden combinar con un bit a bit `OR`.

## <a name="requirements"></a>Requisitos

Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también

- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)