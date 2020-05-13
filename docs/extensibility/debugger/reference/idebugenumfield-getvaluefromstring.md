---
title: IDebugEnumField::GetValueFromString ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bb340721c9f446b740c2723dc3f6dc05452e74de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730258"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
Este método devuelve el valor asociado con el nombre de una constante de enumeración.

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
[en] Cadena que especifica el nombre para el que se va a obtener el valor. Tenga en cuenta que para C++, se trata de una cadena de caracteres anchos.

`pValue`\
[fuera] Devuelve el valor numérico asociado.

## <a name="return-value"></a>Valor devuelto
 Si se `S_OK`realiza correctamente, devuelve ; de lo `S_FALSE`contrario, devuelve , si el nombre no forma parte de la enumeración o un código de error.

## <a name="remarks"></a>Observaciones
 Este método distingue mayúsculas de minúsculas. Si se necesita una búsqueda sin distinción entre mayúsculas y minúsculas (por ejemplo, en un lenguaje como Visual Basic donde los nombres no distinguen entre mayúsculas y minúsculas), utilice [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md).

## <a name="see-also"></a>Vea también
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)
