---
title: IDebugCustomAttributeQuery2::IsCustomAttributeDefined | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e2ecd70eeeddb4b61d8ed8d307bd579c68ef519
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335825"
---
# <a name="idebugcustomattributequery2iscustomattributedefined"></a>IDebugCustomAttributeQuery2::IsCustomAttributeDefined
Determina si existe un atributo personalizado por su nombre.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT IsCustomAttributeDefined( 
   LPCOLESTR pszCustomAttributeName
);
```

```csharp
int IsCustomAttributeDefined(
   [In] string pszCustomAttributeName
);
```

## <a name="parameters"></a>Parámetros
`pszCustomAttributeName`\
[in] Una cadena que contiene el nombre del atributo personalizado para buscar.

## <a name="return-value"></a>Valor devuelto
 Devuelve que S_OK si el atributo personalizado se define en este campo, en caso contrario, devuelve S_FALSE.

## <a name="remarks"></a>Comentarios
 Para obtener los bytes del atributo asociados con el atributo personalizado, llame a la [GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md) método.

## <a name="see-also"></a>Vea también
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)