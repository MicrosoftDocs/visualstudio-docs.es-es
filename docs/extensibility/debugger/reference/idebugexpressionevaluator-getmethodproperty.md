---
description: Este método obtiene un objeto de propiedad que contiene las variables locales, los argumentos y otras propiedades de un método.
title: 'IDebugExpressionEvaluator:: GetMethodProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e4a82ce250b47f2f199d9e8e8fcf3a2ca7ec5777
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092181"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
Este método obtiene un objeto de propiedad que contiene las variables locales, los argumentos y otras propiedades de un método.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetMethodProperty( 
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   BOOL                  fIncludeHiddenLocals,
   IDebugProperty2**     ppProperty
);
```

```csharp
int GetMethodProperty(
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   int                  fIncludeHiddenLocals,
   out IDebugProperty2  ppProperty
);
```

## <a name="parameters"></a>Parámetros
`pSymbolProvider`\
de Proveedor de símbolos que se va a utilizar, expresado como un objeto [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) .

`pAddress`\
de Dirección en código, expresada como un objeto [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) , que se debe resolver en la función contenedora más cercana.

`pBinder`\
de Enlazador que se va a utilizar, expresado como un objeto [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .

`fIncludeHiddenLocals`\
de Distinto de cero ( `TRUE` ) significa incluir variables locales ocultas; cero ( `FALSE` ) significa dejar las variables locales ocultas

`ppProperty`\
enuncia Devuelve un objeto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que representa el método.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Las variables locales ocultas suelen ser variables generadas por el compilador.

## <a name="see-also"></a>Consulte también
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
