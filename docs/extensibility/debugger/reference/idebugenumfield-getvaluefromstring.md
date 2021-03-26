---
description: Este método devuelve el valor asociado al nombre de una constante de enumeración.
title: 'IDebugEnumField:: GetValueFromString | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ec1070948685c69ce8615e2bef836c4d721e1cb0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092545"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
Este método devuelve el valor asociado al nombre de una constante de enumeración.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetValueFromString(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromString(
   string    pszValue,
   out ulong pValue
);
```

## <a name="parameters"></a>Parámetros
`pszValue`\
de Cadena que especifica el nombre para el que se va a obtener el valor. Tenga en cuenta que para C++, se trata de una cadena de caracteres anchos.

`pValue`\
enuncia Devuelve el valor numérico asociado.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve `S_FALSE` si el nombre no forma parte de la enumeración, o un código de error.

## <a name="remarks"></a>Observaciones
 Este método distingue mayúsculas de minúsculas. Si se necesita una búsqueda que no distinga mayúsculas de minúsculas (por ejemplo, en un lenguaje como Visual Basic donde los nombres no distinguen mayúsculas de minúsculas), use [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md).

## <a name="see-also"></a>Consulte también
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)
