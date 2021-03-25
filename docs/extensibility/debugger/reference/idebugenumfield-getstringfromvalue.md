---
description: Este método obtiene el nombre de la constante de enumeración a partir de su valor.
title: 'IDebugEnumField:: GetStringFromValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 41d004a9b226646dd1196f1debc244cdf11efe32
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092584"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
Este método obtiene el nombre de la constante de enumeración a partir de su valor.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetStringFromValue(
   ULONGLONG value,
   BSTR*     pbstrValue
);
```

```csharp
int GetStringFromValue(
   ulong      value,
   out string pbstrValue
);
```

## <a name="parameters"></a>Parámetros
`value`\
de Valor para el que se va a obtener el nombre de la constante de enumeración.

`pbstrValue`\
enuncia Devuelve el nombre de la constante de enumeración.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve `S_FALSE` si el valor no tiene ningún nombre asociado o devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Si hay más de un nombre asociado al mismo valor, se devolverá el primer nombre definido en la enumeración.

## <a name="see-also"></a>Consulte también
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
