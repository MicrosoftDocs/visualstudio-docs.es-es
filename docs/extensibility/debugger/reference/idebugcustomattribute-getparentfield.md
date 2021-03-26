---
description: Obtiene el campo al que está asociado el atributo personalizado.
title: 'IDebugCustomAttribute:: GetParentField | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7aaa3ea38e5ed0691b8e335a3d39a8a82b7576ef
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088060"
---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
Obtiene el campo al que está asociado el atributo personalizado.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetParentField( 
   IDebugField** ppField
);
```

```csharp
int GetParentField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parámetros
`ppField`\
enuncia Devuelve el objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa el campo al que está asociado el atributo personalizado.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Llame al método [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) en el objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) devuelto para determinar el tipo de campo del elemento primario.

## <a name="see-also"></a>Consulte también
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
