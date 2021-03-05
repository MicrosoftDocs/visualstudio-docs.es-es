---
description: Crea un enumerador para los parámetros del método.
title: 'IDebugMethodField:: EnumParameters | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 51b0ca4d799bc5943a1effd612947b5822730d37
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164999"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
Crea un enumerador para los parámetros del método.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumParameters( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumParameters(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>Parámetros
`ppParams`\
enuncia Devuelve un objeto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa la lista de parámetros para el método. de lo contrario, devuelve un valor NULL si no hay ningún parámetro.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, Devuelve S_OK o devuelve S_FALSE si no hay ningún parámetro. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Cada elemento es un objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa distintos tipos de parámetros. Llame al método [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) en cada objeto para determinar exactamente qué tipo de parámetro representa el objeto.

 Un parámetro incluye el nombre de la variable y su tipo. El primer parámetro de un método de clase suele ser el puntero "this".

 Si solo se necesitan los tipos de los parámetros, llame al método [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) .

## <a name="see-also"></a>Consulte también
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)
