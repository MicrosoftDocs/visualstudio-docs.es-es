---
title: PROVIDER_PROCESS_DATA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bdaf15d09af3199d026155cf7667f063f5bbe858
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713778"
---
# <a name="provider_process_data"></a>PROVIDER_PROCESS_DATA
Esta estructura proporciona información sobre los procesos que se ejecutan en un equipo.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct tagPROVIDER_PROCESS_DATA {
   PROVIDER_FIELDS    Fields;
   PROGRAM_NODE_ARRAY ProgramNodes;
   BOOL               fIsDebuggerPresent;
} PROVIDER_PROCESS_DATA;
```

```csharp
public struct PROVIDER_PROCESS_DATA {
   public uint               Fields;
   public PROGRAM_NODE_ARRAY ProgramNodes;
   public int                fIsDebuggerPresent;
}
```

## <a name="members"></a>Miembros
 `Fields`\
 Combinación de marcas de la enumeración [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) , que indica qué campos se rellenan.

 `ProgramNodes`\
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) estructura que contiene una matriz de nodos de programa.

 `fIsDebuggerPresent`\
 Distinto de cero ( `TRUE` ) si el [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] depurador se está ejecutando, cero ( `FALSE` ) si no lo está.

## <a name="remarks"></a>Observaciones
 Esta estructura se pasa al método [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) donde se rellena.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)
- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
