---
title: DEBUG_CUSTOM_VIEWER de la casa de la Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3de9b8f7ef30cffbdd78399dc831060e413ba51b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737547"
---
# <a name="debug_custom_viewer"></a>DEBUG_CUSTOM_VIEWER
Estructura que identifica un visor personalizado o un visualizador de tipos.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct tagDEBUG_CUSTOM_VIEWER {
    DWORD dwID;
    BSTR  bstrMenuName;
    BSTR  bstrDescription;
    GUID  guidLang;
    GUID  guidVendor;
    BSTR  bstrMetric;
} DEBUG_CUSTOM_VIEWER;
```

```csharp
public struct DEBUG_CUSTOM_VIEWER {
    public uint   dwID;
    public string bstrMenuName;
    public string bstrDescription;
    public Guid   guidLang;
    public Guid   guidVendor;
    public string bstrMetric;
};
```

## <a name="members"></a>Miembros
`dwID`\
Un identificador para diferenciar varios visores o `GUID`visualizadores implementados por uno .

`bstrMenuName`\
El texto que aparecerá en el menú desplegable.

`bstrDescription`\
Una descripción del visor personalizado o del visualizador de tipo (debe ser un valor nulo si no se utiliza).

`guidLang`\
Lenguaje del evaluador de expresiones de proporcionación.

`guidVendor`\
Proveedor del evaluador de expresiones de proporcionación.

`bstrMetric`\
Métrica en la que se `CLSID` almacena el visor personalizado o el visualizador de tipos.

## <a name="remarks"></a>Observaciones
Una lista de esta estructura se devuelve mediante una llamada a la [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) método (y, por extensión, el [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) método).

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
