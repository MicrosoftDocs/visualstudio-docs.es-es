---
title: IDebugEnumField::GetStringFromValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98d7e976e0cd37ad1397666471c89da3d47d45d3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56710375"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
Este método obtiene el nombre de la constante de enumeración dada su valor.

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

#### <a name="parameters"></a>Parámetros
 `value`

 [in] El valor para el que se va a obtener el nombre de la enumeración constante.

 `pbstrValue`

 [out] Devuelve el nombre de la constante de enumeración.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` si el valor no tiene asociado un nombre, o devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Si hay más de un nombre asociado con el mismo valor, se devolverá el nombre definido en la enumeración.

## <a name="see-also"></a>Vea también
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)