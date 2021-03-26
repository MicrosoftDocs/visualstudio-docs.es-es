---
description: Recupera un objeto de servicio a partir de su identificador único.
title: 'IDebugExpressionEvaluator2:: GetService | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a9c595d2a3a4551920e17a9ad8d8a13b5ae4ab0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092012"
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
