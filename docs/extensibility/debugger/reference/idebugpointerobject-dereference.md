---
title: IDebugPointerObject::Dereference ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe87d5db40ce663d84c9561e89a84e6fcb1684ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725566"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Obtiene el objeto señalado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT DeReference( 
   DWORD          dwIndex,
   IDebugObject** ppObject
);
```

```csharp
int Dereference(
   uint             dwIndex,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parámetros
`dwIndex`\
[en] Un desplazamiento de bytes simple desde el principio del objeto al que se apunta.

`ppObject`\
[fuera] Devuelve un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto que representa el objeto señalado, más desplazamiento, si existe.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; de lo contrario, devuelve un código de error. Devuelve E_FAIL si este objeto no apunta a otro objeto.

## <a name="remarks"></a>Observaciones
 El objeto al que se apunta puede ser un tipo primitivo o más complejo, como una clase o estructura.

## <a name="see-also"></a>Vea también
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
