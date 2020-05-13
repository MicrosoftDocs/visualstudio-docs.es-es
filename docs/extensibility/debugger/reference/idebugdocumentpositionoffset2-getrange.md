---
title: IDebugDocumentPositionOffset2::GetRange ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd305b6506471a40de90fbd954e54461d2a139d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731626"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
Recupera el intervalo para la posición actual del documento.

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
[adentro, fuera] Desplazamiento para la posición inicial del rango. Establezca este parámetro en un valor nulo si esta información no es necesaria.

`pdwEndOffset`\
[adentro, fuera] Desplazamiento para la posición final del rango. Establezca este parámetro en un valor nulo si esta información no es necesaria.

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
- [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)
- [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
