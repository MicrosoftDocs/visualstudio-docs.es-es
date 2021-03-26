---
description: Este método convierte una ubicación de método y el desplazamiento en una dirección de memoria.
title: 'IDebugExpressionEvaluator:: GetMethodLocationProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ddc9c17b90be6d65786d58ff2bf585461c4fc69f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092194"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Este método convierte una ubicación de método y el desplazamiento en una dirección de memoria.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetMethodLocationProperty( 
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodLocationProperty(
   string               upstrFullyQualifiedMethodPlusOffset,
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   out IDebugProperty2  ppProperty
);
```

## <a name="parameters"></a>Parámetros
`upstrFullyQualifiedMethodPlusOffset`\
de Ubicación y desplazamiento del método, expresado como una cadena.

`pSymbolProvider`\
de El proveedor de símbolos expresado como un objeto [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) .

`pAddress`\
de Una dirección dentro del método, expresada como un objeto [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

`pBinder`\
de El enlazador expresado como un objeto [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .

`ppProperty`\
enuncia Devuelve una interfaz [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que representa la dirección de memoria.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 La dirección devuelta se puede utilizar para establecer un punto de interrupción, por ejemplo.

 A pesar del nombre `upstrFullyQualifiedMethodPlusOffset` , este parámetro se puede pasar a un nombre de método parcialmente calificado. En ese caso, el método seleccionado es el que se incluye `pAddress` . La forma en que se interpreta este parámetro depende de la implementación del evaluador de expresiones y del lenguaje que admite.

## <a name="see-also"></a>Consulte también
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
