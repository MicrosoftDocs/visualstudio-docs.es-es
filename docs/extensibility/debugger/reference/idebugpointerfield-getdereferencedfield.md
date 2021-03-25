---
description: Este método devuelve el tipo de objeto al que señala este objeto de puntero.
title: 'IDebugPointerField:: GetDereferencedField | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e54b378475cec191ca8395a7af5652ea6e93125f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053677"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
Este método devuelve el tipo de objeto al que señala este objeto de puntero.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetDereferencedField(
   IDebugField** ppField
);
```

```csharp
int GetDereferencedField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parámetros
`ppField`\
enuncia Devuelve un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que describe el tipo de objeto de destino.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Si, por ejemplo, el objeto [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) apunta a un entero, el tipo [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) devuelto por este método describe ese tipo entero.

## <a name="see-also"></a>Consulte también
- [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
