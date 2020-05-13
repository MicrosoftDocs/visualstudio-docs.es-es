---
title: BP_LOCATION_CODE_FUNC_OFFSET Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET
helpviewer_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET structure
ms.assetid: ab38f7ca-fa01-4cf3-a06c-56cbb7207617
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 32331a5b628c27dc79d6a2e5919c8d268c96a3aa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737994"
---
# <a name="bp_location_code_func_offset"></a>BP_LOCATION_CODE_FUNC_OFFSET
Describe la ubicación de desplazamiento de un punto de interrupción en una función en el código.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _BP_LOCATION_CODE_FUNC_OFFSET {
    BSTR                     bstrContext;
    IDebugFunctionPosition2* pFuncPos;
} BP_LOCATION_CODE_FUNC_OFFSET;
```

## <a name="members"></a>Miembros
`bstrContext`\
El contexto del punto de interrupción, normalmente un método o nombre de función como se ve en una pila de llamadas.

`pFuncPos`\
El [iDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md) objeto que describe el nombre de la función y la posición relativa desde el principio de la función.

## <a name="remarks"></a>Observaciones
Esta estructura es un miembro de la estructura [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) como parte de una unión.

El `pFuncPos` miembro indica dónde establecer el punto de interrupción de la función.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)
