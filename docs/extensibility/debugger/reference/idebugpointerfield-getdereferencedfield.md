---
title: IDebugPointerField::GetDereferencedField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a2fed1d2f0a9027f4570c4efdc41ddf1eeb5f9a3
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2019
ms.locfileid: "66209409"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
Este método devuelve el tipo de objeto al que señala este objeto de puntero.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetDereferencedField(
   IDebugField** ppField
);
```

```csharp
int GetDereferencedField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parámetros
`ppField`\
[out] Devuelve un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que describe el tipo de objeto de destino.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Por ejemplo, si la [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) objeto apunta a un entero, el [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) ese tipo entero describe el tipo devuelto por este método.

## <a name="see-also"></a>Vea también
- [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)