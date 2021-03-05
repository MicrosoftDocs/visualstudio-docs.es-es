---
description: Este método convierte una cadena de expresión en una expresión analizada.
title: IDebugExpressionEvaluator::P arse | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f6a586c7e7cac1a4ef034b7941840db59d376180
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152499"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
Este método convierte una cadena de expresión en una expresión analizada.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Parse( 
   LPCOLESTR                upstrExpression,
   PARSEFLAGS               dwFlags,
   UINT                     nRadix,
   BSTR*                    pbstrError,
   UINT*                    pichError,
   IDebugParsedExpression** ppParsedExpression
);
```

```csharp
int Parse(
   string                     upstrExpression,
   enum_PARSEFLAGS            dwFlags,
   uint                       nRadix,
   out string                 pbstrError,
   out uint                   pichError,
   out IDebugParsedExpression ppParsedExpression
);
```

## <a name="parameters"></a>Parámetros
`upstrExpression`\
de Cadena de expresión que se va a analizar.

`dwFlags`\
de Colección de constantes [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) que determinan cómo se va a analizar la expresión.

`nRadix`\
de Base que se va a usar para interpretar cualquier información numérica.

`pbstrError`\
enuncia Devuelve el error como texto legible.

`pichError`\
enuncia Devuelve la posición de carácter del inicio del error en la cadena de expresión.

`ppParsedExpression`\
enuncia Devuelve la expresión analizada en un objeto [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) .

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Este método genera una expresión analizada, no un valor real. Una expresión analizada está lista para su evaluación, es decir, se ha convertido en un valor.

## <a name="see-also"></a>Consulte también
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
