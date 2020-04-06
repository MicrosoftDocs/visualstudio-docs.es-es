---
title: MACHINE_INFO Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO
helpviewer_keywords:
- MACHINE_INFO structure
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad66992bd07afa2ef563c1b58fab0172e9a6121e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714547"
---
# <a name="machine_info"></a>MACHINE_INFO
Describe una máquina en particular.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct tagMACHINE_INFO { 
   MACHINE_INFO_FIELDS Fields;
   BSTR                bstrName;
   MACHINE_INFO_FLAGS  Flags;
} MACHINE_INFO;
```

```csharp
public struct MACHINE_INFO { 
   public uint   Fields;
   public string bstrName;
   public uint   Flags;
};
```

## <a name="members"></a>Miembros
 `Fields`\
 Una combinación de indicadores de la [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) enumeración que especifican qué campos de la estructura se inicializan.

 `bstrName`\
 Nombre de la máquina. Equivalente a llamar a [GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md).

 `Flags`\
 Una combinación de indicadores de la [enumeración MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) que describe los atributos de la máquina.

## <a name="remarks"></a>Observaciones
 Esta estructura se devuelve mediante una llamada a la [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) método.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
