---
description: Este método compara el campo con el campo especificado para determinar si son iguales.
title: 'IDebugField:: Equal | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 58673703fa0e585095c9a82fe2c7a4bc3e14827c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077114"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Este método compara el campo con el campo especificado para determinar si son iguales.

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
de Campo que se va a comparar con este.

## <a name="return-value"></a>Valor devuelto
 Si los campos son iguales, devuelve `S_OK` . Si los campos son diferentes, devuelve `S_FALSE.` en caso contrario, devuelve un código de error.

## <a name="see-also"></a>Consulte también
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
