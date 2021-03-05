---
description: Se usa para establecer puntos de interrupción de datos que se basan en una cadena que el usuario puede especificar desde el entorno de desarrollo integrado (IDE).
title: BP_LOCATION_DATA_STRING | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 1e4a250843ebbb6ab7680040e3aa296699e184ee
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144356"
---
# <a name="bp_location_data_string"></a>BP_LOCATION_DATA_STRING
Se usa para establecer puntos de interrupción de datos que se basan en una cadena que el usuario puede especificar desde el entorno de desarrollo integrado (IDE).

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _BP_LOCATION_DATA_STRING {
    IDebugThread2* pThread;
    BSTR           bstrContext;
    BSTR           bstrDataExpr;
    DWORD          dwNumElements;
} BP_LOCATION_DATA_STRING;
```

## <a name="members"></a>Members
`pThread`\
El objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa el subproceso en el que se produce el punto de interrupción.

`bstrContext`\
Contexto del punto de interrupción en el código, normalmente un nombre de método o función tal y como se ha detectado en una pila de llamadas.

`bstrDataExpr`\
Cadena de datos que especifica el usuario para establecer el punto de interrupción.

`dwNumElements`\
El número de elementos de la cadena de datos en los que se produce el punto de interrupción.

## <a name="remarks"></a>Observaciones
Esta estructura es miembro de la estructura [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) como parte de una Unión.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
