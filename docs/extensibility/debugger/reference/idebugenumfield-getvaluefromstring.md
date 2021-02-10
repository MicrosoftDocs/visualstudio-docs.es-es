---
title: 'IDebugEnumField:: GetValueFromString | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 77cce7a6780c816fbee0ade1c795cb1174e3e7f0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933458"
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

## <a name="remarks"></a>Notas
 Este método distingue mayúsculas de minúsculas. Si se necesita una búsqueda que no distinga mayúsculas de minúsculas (por ejemplo, en un lenguaje como Visual Basic donde los nombres no distinguen mayúsculas de minúsculas), use [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md).

## <a name="see-also"></a>Vea también
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)
