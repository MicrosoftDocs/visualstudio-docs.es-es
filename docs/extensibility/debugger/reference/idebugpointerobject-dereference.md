---
title: IDebugPointerObject::Dereference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 90a5a1f6fca718397654e836f41089b122425f0f
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2019
ms.locfileid: "66209381"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Obtiene el objeto al que señala.

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
[in] Desplazamiento de bytes simple desde el principio del objeto que apunta.

`ppObject`\
[out] Devuelve un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) de objeto que representa el objeto señalado, además de desplazamiento, si existe.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error. Devuelve E_FAIL si este objeto no apunta a otro objeto.

## <a name="remarks"></a>Comentarios
 Puede ser el objeto al que señala a un tipo primitivo o un tipo más complejo como una clase o estructura.

## <a name="see-also"></a>Vea también
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)