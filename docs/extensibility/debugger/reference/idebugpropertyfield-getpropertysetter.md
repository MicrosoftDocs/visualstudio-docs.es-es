---
title: IDebugPropertyField::GetPropertySetter | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField::GetPropertySetter
helpviewer_keywords:
- IDebugPropertyField::GetPropertySetter method
ms.assetid: 744d76fd-2bcc-4917-a040-ce4cc714ef61
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29772ad76df6538ec5093d2fb34427a7fa89c5ff
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345680"
---
# <a name="idebugpropertyfieldgetpropertysetter"></a>IDebugPropertyField::GetPropertySetter
Obtiene el método que establece la propiedad.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetPropertySetter( 
   IDebugMethodField** ppField
);
```

```csharp
int GetPropertySetter(
   out IDebugMethodField ppField
);
```

## <a name="parameters"></a>Parámetros
`ppField`\
[out] Devuelve un [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) objeto que representa el método que establece la propiedad.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Para obtener el método que obtiene la propiedad, llame a la [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md) método.

## <a name="see-also"></a>Vea también
- [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)