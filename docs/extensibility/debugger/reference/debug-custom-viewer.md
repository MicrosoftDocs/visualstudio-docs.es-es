---
description: Estructura que identifica un visor personalizado o un visualizador de tipos.
title: DEBUG_CUSTOM_VIEWER | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 76c02956acd9277f203c67bede7369d6bb7a603a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096283"
---
# <a name="debug_custom_viewer"></a>DEBUG_CUSTOM_VIEWER
Estructura que identifica un visor personalizado o un visualizador de tipos.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct tagDEBUG_CUSTOM_VIEWER {
    DWORD dwID;
    BSTR  bstrMenuName;
    BSTR  bstrDescription;
    GUID  guidLang;
    GUID  guidVendor;
    BSTR  bstrMetric;
} DEBUG_CUSTOM_VIEWER;
```

```csharp
public struct DEBUG_CUSTOM_VIEWER {
    public uint   dwID;
    public string bstrMenuName;
    public string bstrDescription;
    public Guid   guidLang;
    public Guid   guidVendor;
    public string bstrMetric;
};
```

## <a name="members"></a>Miembros
`dwID`\
IDENTIFICADOR para diferenciar varios visores o visualizadores implementados por uno `GUID` .

`bstrMenuName`\
Texto que aparecerá en el menú desplegable.

`bstrDescription`\
Una descripción del visor personalizado o del visualizador de tipos (debe ser un valor NULL si no se usa).

`guidLang`\
Lenguaje del evaluador de expresiones que proporciona.

`guidVendor`\
Proveedor del evaluador de expresiones que proporciona.

`bstrMetric`\
Métrica en la que se almacena el visualizador personalizado o el visualizador de tipos `CLSID` .

## <a name="remarks"></a>Observaciones
Una llamada al método [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) devuelve una lista de esta estructura (y, por extensión, el método [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) ).

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
