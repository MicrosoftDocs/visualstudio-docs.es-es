---
title: BP_LOCATION_CODE_FUNC_OFFSET | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET
helpviewer_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET structure
ms.assetid: ab38f7ca-fa01-4cf3-a06c-56cbb7207617
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 25ac9881f44019d818c49091900ce759680a37a5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319073"
---
# <a name="bplocationcodefuncoffset"></a>BP_LOCATION_CODE_FUNC_OFFSET
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
El contexto del punto de interrupción, normalmente un nombre de método o una función como se muestra en una pila de llamadas.

`pFuncPos`\
El [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md) objeto que describe el nombre de la función y la posición relativa desde el principio de la función.

## <a name="remarks"></a>Comentarios
Esta estructura es un miembro de la [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) estructura como parte de una unión.

El `pFuncPos` miembro indica dónde se establecerá el punto de interrupción de función.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)
