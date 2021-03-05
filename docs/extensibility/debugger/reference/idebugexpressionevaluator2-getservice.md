---
description: Recupera un objeto de servicio a partir de su identificador único.
title: 'IDebugExpressionEvaluator2:: GetService | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a522cefec514baf8b7d8219846587f18c37559a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152369"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
Recupera un objeto de servicio a partir de su identificador único.

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
de Identificador único del servicio que se va a recuperar.

`ppService`\
enuncia Devuelve un objeto que representa el servicio.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Puede ser utilizado por un evaluador de expresiones de terceros para obtener servicios de otro evaluador de expresiones. Por ejemplo, este método se puede utilizar para obtener la interfaz del servicio visualizador del evaluador de expresiones predeterminado. Es improbable que los evaluadores de expresiones de terceros deban implementar esta interfaz.

## <a name="see-also"></a>Consulte también
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
