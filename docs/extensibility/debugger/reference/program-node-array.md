---
title: PROGRAM_NODE_ARRAY | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROGRAM_NODE_ARRAY
helpviewer_keywords:
- PROGRAM_NODE_ARRAY structure
ms.assetid: 8eeea600-eda5-4b7c-868a-0b86d177b0a5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ac5a891912d84a719a8bf475724f0b1cb7d685d4
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457943"
---
# <a name="programnodearray"></a>PROGRAM_NODE_ARRAY
Contiene una matriz de objetos que describen los programas de interés.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct tagPROGRAM_NODE_ARRAY {
   DWORD                dwCount;
   IDebugProgramNode2** Members;
} PROGRAM_NODE_ARRAY;
```

```csharp
public struct tagPROGRAM_NODE_ARRAY {
   public uint                 dwCount;
   public IDebugProgramNode2[] Members;
}
```

## <a name="members"></a>Miembros
 `dwCount`\
 Número de objetos de la `Members` matriz.

 `Members`\
 Una matriz de [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objetos que describen los programas que se solicita.

## <a name="remarks"></a>Comentarios
 Esta estructura es parte de la [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) estructura que a su vez se rellena mediante una llamada a la [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) método.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)