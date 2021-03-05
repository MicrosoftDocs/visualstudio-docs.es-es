---
description: Este método evalúa la expresión analizada y, opcionalmente, convierte el resultado en otro tipo de datos.
title: 'IDebugParsedExpression:: EvaluateSync | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression::EvaluateSync
helpviewer_keywords:
- IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 99760fb35975834186beddf2962ea8402543d088
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143110"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
Este método evalúa la expresión analizada y, opcionalmente, convierte el resultado en otro tipo de datos.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EvaluateSync( 
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   BSTR                  bstrResultType,
   IDebugProperty2**     ppResult
);
```

```csharp
int EvaluateSync(
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   string               bstrResultType,
   out IDebugProperty2  ppResult
);
```

## <a name="parameters"></a>Parámetros
`dwEvalFlags`\
de Combinación de constantes de [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) que controlan cómo se va a evaluar la expresión.

`dwTimeout`\
de Especifica el tiempo máximo, en milisegundos, que se va a esperar antes de que se devuelva desde este método. Use `INFINITE` para esperar indefinidamente.

`pSymbolProvider`\
de El proveedor de símbolos, expresado como una interfaz [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) .

`pAddress`\
de La ubicación de ejecución actual dentro de un método, expresada como una interfaz [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

`pBinder`\
de El enlazador, expresado como una interfaz [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .

`bstrResultType`\
de Tipo al que se debe convertir el resultado. Este argumento puede ser un valor null.

`ppResult`\
enuncia Devuelve la interfaz [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que representa los resultados de la evaluación.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El contexto de evaluación de expresión lo proporciona `pAddress` , lo que permite determinar el método contenedor y, a continuación, usar reglas de ámbito de lenguaje para determinar el valor de los símbolos en la expresión.

## <a name="see-also"></a>Consulte también
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
