---
title: IDebugEnumField::GetValueFromStringCaseInsensitive | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 72e6f79616c8c8099b938a29bc1d1809adb152a3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350065"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
Este método usa una búsqueda de mayúsculas y minúsculas para devolver el valor asociado con el nombre de una constante de enumeración.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetValueFromStringCaseInsensitive(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromStringCaseInsensitive(
   string    pszValue,
   out ulong pValue
);
```

## <a name="parameters"></a>Parámetros
`pszValue`\
[in] Cadena que especifica el nombre para el que se va a obtener el valor. Tenga en cuenta que en C++, esto es una cadena de caracteres anchos.

`pValue`\
[out] Devuelve el valor numérico asociado.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE`, si el nombre no es parte de la enumeración o un código de error.

## <a name="remarks"></a>Comentarios
 Este método distingue mayúsculas de minúsculas. Si es necesaria una búsqueda distingue mayúsculas de minúsculas (por ejemplo, en un lenguaje como C++, donde los nombres distinguen mayúsculas de minúsculas), utilice [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).

## <a name="see-also"></a>Vea también
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)