---
title: IDebugExpressionEvaluator2::GetService ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5428606ad54c7938037c3ffecf04f1cfe41787c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729352"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
Recupera un objeto de servicio dado su identificador único.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetService (
   GUID        uid,
   IUnknown ** ppService
);
```

```csharp
int GetService (
   Guid       uid,
   out object ppService
);
```

## <a name="parameters"></a>Parámetros
`uid`\
[en] Identificador único del servicio que se va a recuperar.

`ppService`\
[fuera] Devuelve un objeto que representa el servicio.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Esto lo puede consumir un evaluador de expresiones de terceros para obtener servicios de otro evaluador de expresiones. Por ejemplo, este método podría utilizarse para obtener la interfaz para el servicio de visualizador desde el evaluador de expresiones predeterminado. Es poco probable que los evaluadores de expresiones de terceros necesiten implementar esta interfaz.

## <a name="see-also"></a>Vea también
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
