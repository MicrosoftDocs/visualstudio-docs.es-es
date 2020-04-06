---
title: IDebugExpressionEvaluator::GetMethodProperty ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ebcf24ee39505091ff79c1f2f31d505217f77efb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729505"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
Este método obtiene un objeto de propiedad que contiene los valores locales, argumentos y otras propiedades de un método.

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
[en] El proveedor de símbolos que se va a usar, expresado como un [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) objeto.

`pAddress`\
[en] La dirección en el código, expresado como un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objeto, que debe resolverse a la función contenedora más cercana.

`pBinder`\
[en] El enlazador que se va a usar, expresado como un [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) objeto.

`fIncludeHiddenLocals`\
[en] Distinto de`TRUE`cero ( )significa incluir locales ocultos; cero`FALSE`( ) significa dejar fuera a los lugareños ocultos

`ppProperty`\
[fuera] Devuelve un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto que representa el método.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Las variables locales ocultas suelen ser variables generadas por el compilador.

## <a name="see-also"></a>Vea también
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
