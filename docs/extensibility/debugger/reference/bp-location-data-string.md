---
title: BP_LOCATION_DATA_STRING de la casa de la casa de Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 75f881feaaa2068abd98d771a63024f20435d98f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737970"
---
# <a name="bp_location_data_string"></a>BP_LOCATION_DATA_STRING
Se utiliza para establecer puntos de interrupción de datos que se basan en una cadena que el usuario puede escribir desde el entorno de desarrollo integrado (IDE).

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _BP_LOCATION_DATA_STRING {
    IDebugThread2* pThread;
    BSTR           bstrContext;
    BSTR           bstrDataExpr;
    DWORD          dwNumElements;
} BP_LOCATION_DATA_STRING;
```

## <a name="members"></a>Miembros
`pThread`\
El [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa el subproceso en el que se produce el punto de interrupción.

`bstrContext`\
El contexto del punto de interrupción dentro del código, normalmente un método o nombre de función como se ve en una pila de llamadas.

`bstrDataExpr`\
La cadena de datos que el usuario escribe para establecer el punto de interrupción.

`dwNumElements`\
El número de elementos de la cadena de datos en la que se produce el punto de interrupción.

## <a name="remarks"></a>Observaciones
Esta estructura es un miembro de la estructura [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) como parte de una unión.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
