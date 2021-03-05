---
description: Recupera el intervalo para la posición del documento actual.
title: 'IDebugDocumentPositionOffset2:: GetRange | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c56ac73d85f9cfbfdc17d40da9f0fec415e057d7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154241"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
Recupera el intervalo para la posición del documento actual.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetRange(
   DWORD* pdwBegOffset,
   DWORD* pdwEndOffset
);
```

```csharp
public int GetRange(
   ref uint pdwBegOffset,
   ref uint pdwEndOffset
);
```

## <a name="parameters"></a>Parámetros
`pdwBegOffset`\
[in, out] Desplazamiento de la posición inicial del intervalo. Establezca este parámetro en un valor NULL si no se necesita esta información.

`pdwEndOffset`\
[in, out] Desplazamiento para la posición final del intervalo. Establezca este parámetro en un valor NULL si no se necesita esta información.

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
- [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)
- [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
