---
title: IDebugEngine2::SetMetric ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: caada8db1791d94e7a9632394cd4659bf8cec3a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730899"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
Este método establece un valor del Registro conocido como métrica.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetMetric(
   LPCOLESTR pszMetric,
   VARIANT   varValue
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
[en] El nombre de la métrica.

`varValue`\
[en] Especifica el valor de la métrica.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Una métrica es un valor del Registro que se usa para cambiar el comportamiento de un motor de depuración o para anunciar la funcionalidad admitida. Este método puede reenviar la llamada a la forma adecuada `SetMetric`de la función auxiliares de SDK para [depurar,](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) .

## <a name="see-also"></a>Vea también
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Asistentes de SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
