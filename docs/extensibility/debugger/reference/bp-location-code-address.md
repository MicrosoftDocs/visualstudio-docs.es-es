---
title: BP_LOCATION_CODE_ADDRESS Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_ADDRESS
helpviewer_keywords:
- BP_LOCATION_CODE_ADDRESS structure
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: c215630e522adabdbd285e00d4bcd87cae22a931
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738039"
---
# <a name="bp_location_code_address"></a>BP_LOCATION_CODE_ADDRESS
Describe la ubicación de un punto de interrupción en una dirección en el código.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _BP_LOCATION_CODE_ADDRESS {
    BSTR bstrContext;
    BSTR bstrModuleUrl;
    BSTR bstrFunction;
    BSTR bstrAddress;
} BP_LOCATION_CODE_ADDRESS;
```

## <a name="members"></a>Miembros
`bstrContext`\
El contexto del punto de interrupción, normalmente un método o nombre de función como se ve en una pila de llamadas.

`bstrModuleUrl`\
La dirección URL del módulo que contiene el punto de interrupción.

`bstrFunction`\
El nombre de la función que contiene el punto de interrupción.

`bstrAddress`\
La dirección del punto de interrupción, que se analiza mediante un evaluador de expresiones para enlazarlo a un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objeto.

## <a name="remarks"></a>Observaciones
Esta estructura es un miembro de la estructura [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) como parte de una unión.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
