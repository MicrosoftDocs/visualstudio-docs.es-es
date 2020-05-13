---
title: IDebugDocumentPosition2::GetRange ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a923691afdfe145931ab31d0e9bbc6142e7c8d1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731663"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
Obtiene el intervalo para esta posición de documento.

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
[adentro, fuera] Una [estructura TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) que se rellena con la posición inicial. Establezca este argumento en un valor nulo si esta información no es necesaria.

`pEndPosition`\
[adentro, fuera] Una [estructura TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) que se rellena con la posición final. Establezca este argumento en un valor nulo si esta información no es necesaria.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 El motor de depuración (DE) utiliza el intervalo especificado en una posición de documento para un punto de interrupción de ubicación para buscar por delante una instrucción que realmente aporte código. Por ejemplo, considere el siguiente código:

```
Line 5: // comment
Line 6: x = 1;
```

 La línea 5 no aporta ningún código al programa que se está depurando. Si el depurador que establece el punto de interrupción en la línea 5 desea que la DE busque una cantidad determinada para la primera línea que aporta código, el depurador especificaría un intervalo que incluya líneas candidatas adicionales donde un punto de interrupción podría colocarse correctamente. A continuación, el DE buscaría hacia delante a través de esas líneas hasta que encontrara una línea que pudiera aceptar un punto de interrupción.

## <a name="see-also"></a>Vea también
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
