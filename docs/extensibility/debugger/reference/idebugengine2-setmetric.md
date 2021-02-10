---
title: 'IDebugEngine2:: SetMetric | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4bb3c01b28f2d2c6e90616d389d9858d3346db72
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933523"
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

## <a name="remarks"></a>Notas
 Una métrica es un valor del registro que se usa para cambiar el comportamiento de un motor de depuración o para anunciar la funcionalidad admitida. Este método puede reenviar la llamada al formulario adecuado de las [aplicaciones auxiliares de SDK para la función de depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) , `SetMetric` .

## <a name="see-also"></a>Vea también
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Asistentes de SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
