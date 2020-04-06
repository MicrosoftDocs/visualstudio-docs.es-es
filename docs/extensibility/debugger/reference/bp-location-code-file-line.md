---
title: BP_LOCATION_CODE_FILE_LINE Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_FILE_LINE
helpviewer_keywords:
- BP_LOCATION_CODE_FILE_LINE structure
ms.assetid: 3ff32032-d412-44d3-91bf-870cc354a09e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: e338c3b24ade2cf7663b77abea64f58425d3a068
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738013"
---
# <a name="bp_location_code_file_line"></a>BP_LOCATION_CODE_FILE_LINE
Contiene los datos de la ubicación de un punto de interrupción en una línea específica de un archivo de código fuente.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _BP_LOCATION_CODE_FILE_LINE {
    BSTR                     bstrContext;
    IDebugDocumentPosition2* pDocPos;
} BP_LOCATION_CODE_FILE_LINE;
```

## <a name="members"></a>Miembros
`bstrContext`\
El contexto del punto de interrupción, normalmente un método o nombre de función como se ve en una pila de llamadas.

`pDocPos`\
El [objeto IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) que representa la posición del documento del punto de interrupción.

## <a name="remarks"></a>Observaciones
Esta estructura es un miembro de la estructura [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) como parte de una unión.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
