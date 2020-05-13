---
title: IDebugProgramNodeAttach2::OnAttach ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dfb8a39af3c030dadddcb148a79a96b57f20e183
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721875"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Se adjunta al programa asociado o aplaza el proceso de conexión al método [Attach.](../../../extensibility/debugger/reference/idebugengine2-attach.md)

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT OnAttach(
   [in] REFGUID guidProgramId
);
```

```csharp
int OnAttach(
   ref Guid guidProgramId
};
```

## <a name="parameters"></a>Parámetros
`guidProgramId`\
[en] `GUID` para asignar al programa asociado.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se debe llamar al método [Attach.](../../../extensibility/debugger/reference/idebugengine2-attach.md) De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Se llama a este método durante el proceso de asociación, antes de que el [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) se llama al método. El `OnAttach` método puede realizar el propio proceso de `S_FALSE`conexión (en cuyo caso, `IDebugEngine2::Attach` este `OnAttach` método `S_OK`devuelve ) o aplazar el proceso de conexión al método (el método devuelve ). En cualquier caso, el `OnAttach` `GUID` método puede establecer el programa `GUID`que se está depurando en el archivo .

## <a name="see-also"></a>Vea también
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
