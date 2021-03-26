---
description: Se usa para establecer puntos de interrupción de código basados en una cadena que el usuario puede especificar desde el entorno de desarrollo integrado (IDE).
title: BP_LOCATION_CODE_STRING | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_STRING
helpviewer_keywords:
- BP_LOCATION_CODE_STRING structure
ms.assetid: a4cd71c6-5052-45fe-907b-ebc6ca1df2e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 9c32a75e4976a81498033a656461d897e4f298a3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096777"
---
# <a name="bp_location_code_string"></a>BP_LOCATION_CODE_STRING
Se usa para establecer puntos de interrupción de código basados en una cadena que el usuario puede especificar desde el entorno de desarrollo integrado (IDE).

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _BP_LOCATION_CODE_STRING {
    BSTR bstrContext;
    BSTR bstrCodeExpr;
} BP_LOCATION_CODE_STRING;
```

## <a name="members"></a>Miembros
`bstrContext`\
Contexto del punto de interrupción en el código, normalmente un nombre de método o función tal y como se ha detectado en una pila de llamadas.

`bstrCodeExpr`\
Cadena en la que el usuario escribe para describir el punto de interrupción de código.

## <a name="remarks"></a>Observaciones
Esta estructura es miembro de la estructura [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) como parte de una Unión.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
