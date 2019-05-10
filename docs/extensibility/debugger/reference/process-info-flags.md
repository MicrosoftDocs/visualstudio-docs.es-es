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
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 55157ab9a045b404175369e9682c525929f5e624
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460830"
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

## <a name="fields"></a>Campos

`PIFLAG_SYSTEM_PROCESS`\
Indica que el proceso es un proceso del sistema.

`PIFLAG_DEBUGGER_ATTACHED`\
Indica que el proceso se está depurando un depurador. Puede ser un [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] depurador, o bien puede ser algún otro depurador, por ejemplo, WinDbg.

`PIFLAG_PROCESS_STOPPED`\
Indica que el proceso se detiene. Sólo es válido si `PIFLAG_DEBUGGER_ATTACHED` también se especifica. Disponible en Visual Studio 2005 y versiones posteriores.

`PIFLAG_PROCESS_RUNNING`\
Indica que se está ejecutando el proceso. Sólo es válido si `PIFLAG_DEBUGGER_ATTACHED` también se especifica. Disponible en Visual Studio 2005 y versiones posteriores.

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