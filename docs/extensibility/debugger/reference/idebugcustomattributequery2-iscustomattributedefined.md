---
description: Determina si un atributo personalizado existe por nombre.
title: 'IDebugCustomAttributeQuery2:: IsCustomAttributeDefined | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 646fe46f9d83a320423136b8601ee56b3f4ac583
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077595"
---
# <a name="idebugcustomattributequery2iscustomattributedefined"></a>IDebugCustomAttributeQuery2::IsCustomAttributeDefined
Determina si un atributo personalizado existe por nombre.

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
de Cadena que contiene el nombre del atributo personalizado que se va a buscar.

## <a name="return-value"></a>Valor devuelto
 Devuelve S_OK si el atributo personalizado está definido en este campo; de lo contrario, devuelve S_FALSE.

## <a name="remarks"></a>Observaciones
 Para obtener los bytes de atributo asociados al atributo personalizado, llame al método [getcustomattributebyname (](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md) .

## <a name="see-also"></a>Consulte también
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
