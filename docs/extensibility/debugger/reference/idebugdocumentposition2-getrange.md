---
description: Obtiene el intervalo para esta posición del documento.
title: 'IDebugDocumentPosition2:: GetRange | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5e886891c0d971bdad0916d5b243993e46a7ba57
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162724"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
Obtiene el intervalo para esta posición del documento.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetRange( 
   TEXT_POSITION* pBegPosition,
   TEXT_POSITION* pEndPosition
);
```

```csharp
int GetRange( 
   TEXT_POSITION[] pBegPosition,
   TEXT_POSITION[] pEndPosition
);
```

## <a name="parameters"></a>Parámetros
`pBegPosition`\
[in, out] [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estructura que se rellena con la posición inicial. Establezca este argumento en un valor NULL si no se necesita esta información.

`pEndPosition`\
[in, out] [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estructura que se rellena con la posición final. Establezca este argumento en un valor NULL si no se necesita esta información.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El intervalo especificado en una posición de documento para un punto de interrupción de ubicación lo usa el motor DE depuración (DE) para buscar una instrucción que realmente aporta código. Por ejemplo, considere el siguiente código:

```
Line 5: // comment
Line 6: x = 1;
```

 La línea 5 no aporta ningún código al programa que se está depurando. Si el depurador que establece el punto de interrupción en la línea 5 quiere que el DE busque hacia delante una cantidad determinada para la primera línea que contribuye con el código, el depurador especificaría un intervalo que incluye líneas candidatas adicionales donde un punto de interrupción podría estar correctamente colocado. DE ese punto, buscaría hacia delante a través de esas líneas hasta encontrar una línea que pudiera aceptar un punto de interrupción.

## <a name="see-also"></a>Consulte también
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
