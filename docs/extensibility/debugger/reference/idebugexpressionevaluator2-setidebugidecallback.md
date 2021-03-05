---
description: Permite a un motor de depuración pasar una devolución de llamada al evaluador de expresiones durante la inicialización.
title: 'IDebugExpressionEvaluator2:: SetIDebugIDECallback | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetIDebugIDECallback
- SetIDebugIDECallback
ms.assetid: f01c40ad-ef4b-477b-8304-602c6972bc88
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 827e8a2096b0ac79720e5306cce83c55267269c6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152265"
---
# <a name="idebugexpressionevaluator2setidebugidecallback"></a>IDebugExpressionEvaluator2::SetIDebugIDECallback
Permite a un motor de depuración pasar una devolución de llamada al evaluador de expresiones durante la inicialización.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetIDebugIDECallback (
   IDebugIDECallback * pCallback
);
```

```csharp
int SetIDebugIDECallback (
   IDebugIDECallback pCallback
);
```

## <a name="parameters"></a>Parámetros
`pCallback`\
de Interfaz para la devolución de llamada.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Consulte también
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
