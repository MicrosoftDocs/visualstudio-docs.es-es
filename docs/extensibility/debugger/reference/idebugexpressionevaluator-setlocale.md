---
description: Este método establece el idioma que se va a usar para crear resultados imprimibles.
title: 'IDebugExpressionEvaluator:: SetLocale | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::SetLocale
helpviewer_keywords:
- IDebugExpressionEvaluator::SetLocale method
ms.assetid: d3d2027d-74e2-4ae6-bcc7-59d12f873b7c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f833311fe9029931c0d56cbe828bd027c45c26a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092064"
---
# <a name="idebugexpressionevaluatorsetlocale"></a>IDebugExpressionEvaluator::SetLocale
Este método establece el idioma que se va a usar para crear resultados imprimibles.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetLocale( 
   WORD wLangID
);
```

```csharp
int SetLocale(
   ushort wLangID
);
```

## <a name="parameters"></a>Parámetros
`wLangID`\
de Identificador de idioma.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Se puede llamar a este método muchas veces mientras se carga el evaluador de expresiones (EE), por lo que el EE debe ser capaz de cambiar de idioma sobre la marcha. El EE usa esta configuración regional para devolver mensajes de error y cadenas en el idioma adecuado.

## <a name="see-also"></a>Consulte también
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
