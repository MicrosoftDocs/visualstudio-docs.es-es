---
title: 'IDebugProgramPublisher2:: UnpublishProgram | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721585"
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
Hace que un programa no esté disponible para su depuración.

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
de `IUnknown` Interfaz para el programa. Este es el mismo valor que se proporciona al método [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) y identifica de forma única el programa que se va a quitar (es decir, se usa como una cookie).

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Para que un programa esté disponible para los motores de depuración y el administrador de depuración de sesión, utilice el método [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) .

## <a name="see-also"></a>Vea también
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)
