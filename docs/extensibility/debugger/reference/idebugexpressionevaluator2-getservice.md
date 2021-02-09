---
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
ms.openlocfilehash: fb0f822011a5f54cf97e58f53ec1cf03b5d26a23
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926345"
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

## <a name="remarks"></a>Notas
 Puede ser utilizado por un evaluador de expresiones de terceros para obtener servicios de otro evaluador de expresiones. Por ejemplo, este método se puede utilizar para obtener la interfaz del servicio visualizador del evaluador de expresiones predeterminado. Es improbable que los evaluadores de expresiones de terceros deban implementar esta interfaz.

## <a name="see-also"></a>Vea también
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
