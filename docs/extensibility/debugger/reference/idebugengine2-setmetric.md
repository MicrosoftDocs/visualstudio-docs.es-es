---
description: Este método establece un valor del registro conocido como una métrica.
title: 'IDebugEngine2:: SetMetric | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ec947a97506283b6d26f0e4cb26b06afb183dd57
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087891"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
Este método establece un valor del registro conocido como una métrica.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetMetric(
   LPCOLESTR pszMetric,
   VARIANT   varValue
);
```

```csharp
int SetMetric(
   string pszMetric,
   object varValue
);
```

## <a name="parameters"></a>Parámetros
`pszMetric`\
de El nombre de la métrica.

`varValue`\
de Especifica el valor de métrica.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Una métrica es un valor del registro que se usa para cambiar el comportamiento de un motor de depuración o para anunciar la funcionalidad admitida. Este método puede reenviar la llamada al formulario adecuado de las [aplicaciones auxiliares de SDK para la función de depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) , `SetMetric` .

## <a name="see-also"></a>Consulte también
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Asistentes de SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
