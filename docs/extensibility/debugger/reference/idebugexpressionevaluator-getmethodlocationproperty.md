---
title: IDebugExpressionEvaluator::GetMethodLocationProperty ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6ba87d6c1a1f7370ce5e209440589f362b87035
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729523"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Este método convierte una ubicación del método y desplazamiento en una dirección de memoria.

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
[en] La ubicación del método y el desplazamiento, expresado según una cadena.

`pSymbolProvider`\
[en] El proveedor de símbolos expresado como un [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) objeto.

`pAddress`\
[en] Una dirección dentro del método, expresada como un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objeto.

`pBinder`\
[en] El enlazador expresado como un [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) objeto.

`ppProperty`\
[fuera] Devuelve un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfaz que representa la dirección de memoria.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 La dirección devuelta se puede utilizar para establecer un punto de interrupción, por ejemplo.

 A pesar `upstrFullyQualifiedMethodPlusOffset`del nombre , este parámetro se puede pasar un nombre de método parcialmente calificado. En ese caso, el método seleccionado es `pAddress`el que encierra . La forma en que se interpreta este parámetro depende de la implementación del evaluador de expresiones y del lenguaje que admite.

## <a name="see-also"></a>Vea también
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
