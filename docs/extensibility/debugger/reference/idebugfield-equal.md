---
title: IDebugField::Equal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bfee65537512398cad2f4b86d51ebefac230fb1c
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212229"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Este método compara este campo con el campo especificado para la igualdad.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Equal( 
   IDebugField* pField
);
```

```csharp
int Equal(
   IDebugField pField
);
```

## <a name="parameters"></a>Parámetros
`pField`\
[in] El campo para comparar a ésta.

## <a name="return-value"></a>Valor devuelto
 Si los campos son iguales, devuelve `S_OK`. Si los campos son diferentes, devuelve `S_FALSE.` en caso contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)