---
title: BP_LOCATION_CODE_FUNC_OFFSET | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET
helpviewer_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET structure
ms.assetid: ab38f7ca-fa01-4cf3-a06c-56cbb7207617
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 93296770597e8809c5b739b46d8eaefdc8fe5daf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870290"
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

## <a name="members"></a>Members
`bstrContext`\
Contexto del punto de interrupción, normalmente un nombre de método o función tal y como se ha detectado en una pila de llamadas.

`pFuncPos`\
El objeto [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md) que describe el nombre de la función y la posición relativa desde el principio de la función.

## <a name="remarks"></a>Notas
Esta estructura es miembro de la estructura [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) como parte de una Unión.

El `pFuncPos` miembro indica dónde establecer el punto de interrupción de la función.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)
