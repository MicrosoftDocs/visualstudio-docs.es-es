---
title: IDebugProgramPublisher2::UnpublishProgramNode ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgramNode
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgramNode
ms.assetid: 57c7e6e1-b84e-4e14-ad83-cbbb64e2f526
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ae2c3d9f3c9f6c500b10f580035312b2d045689a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721577"
---
# <a name="idebugprogrampublisher2unpublishprogramnode"></a>IDebugProgramPublisher2::UnpublishProgramNode
Quita un nodo de programa especificado de la disponibilidad a los motores de depuración (DE) y el administrador de depuración de sesión (SDM).

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT UnpublishProgramNode(
   IDebugProgramNode2* pProgramNode
);
```

```csharp
int UnpublishProgramNode(
   IDebugProgramNode2 pProgramNode
);
```

## <a name="parameters"></a>Parámetros
`pProgramNode`\
[en] Un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objeto que representa el nodo de programa que se quita.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Una vez eliminado, el nodo del programa ya no está disponible para consultar la información del programa.

 Para que un nodo de programa esté disponible, llame al método [PublishProgramNode.](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)

## <a name="see-also"></a>Vea también
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)
