---
title: IDebugPortNotify2::AddProgramNode ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2::AddProgramNode
helpviewer_keywords:
- IDebugPortNotify2::AddProgramNode
ms.assetid: 34c0e949-1eb9-4108-9cb8-a3eb87fcf190
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9090c39d85519435d17c940ad21fd55d26904765
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724987"
---
# <a name="idebugportnotify2addprogramnode"></a>IDebugPortNotify2::AddProgramNode
Registra un programa que se puede depurar con el puerto en el que se ejecuta.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT AddProgramNode( 
   IDebugProgramNode2* pProgramNode
);
```

```csharp
int AddProgramNode( 
   IDebugProgramNode2 pProgramNode
);
```

## <a name="parameters"></a>Parámetros
`pProgramNode`\
[en] Un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objeto que representa el programa que se va a registrar.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Un nodo de programa se puede anular el registro del puerto mediante una llamada a la [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) método.

## <a name="see-also"></a>Vea también
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)
