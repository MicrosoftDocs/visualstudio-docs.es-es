---
title: IDebugPointerObject::D ereference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9b3646df80dc93d3248c698efb172bb12a09925e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869640"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Obtiene el objeto al que se apunta.

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
de Desplazamiento de bytes simple desde el principio del objeto al que se apunta.

`ppObject`\
enuncia Devuelve un objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa el objeto al que se apunta, más el desplazamiento, si existe.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error. Devuelve E_FAIL si este objeto no apunta a otro objeto.

## <a name="remarks"></a>Notas
 El objeto al que se señala puede ser un tipo primitivo o más complejo, como una clase o estructura.

## <a name="see-also"></a>Vea también
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
