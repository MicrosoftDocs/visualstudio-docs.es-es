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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8601be6a1c87fcad10c6e5260e791fcf2ce42f01
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153344"
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
