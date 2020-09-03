---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1f00b209ff5f91d160e89f5f55ad966fbe9e6414
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726013"
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

## <a name="see-also"></a>Vea también
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
