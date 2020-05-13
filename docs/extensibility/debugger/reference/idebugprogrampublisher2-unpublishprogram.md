---
title: IDebugProgramPublisher2::UnpublishProgram ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fa3d111559a2c82fe36def202e5c1cf120c5202
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721585"
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
Hace que un programa no esté disponible para ser depurado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT UnpublishProgram(
   IUnknown* pDebuggeeInterface
);
```

```csharp
int UnpublishProgram(
   object pDebuggeeInterface
);
```

## <a name="parameters"></a>Parámetros
`pDebuggeeInterface`\
[en] Una `IUnknown` interfaz para el programa. Este es el mismo valor proporcionado al método [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) e identifica de forma única el programa que se va a quitar (es decir, se usa como cookie).

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Para que un programa esté disponible para los motores de depuración y el administrador de depuración de sesión, utilice el método [PublishProgram.](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)

## <a name="see-also"></a>Vea también
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)
