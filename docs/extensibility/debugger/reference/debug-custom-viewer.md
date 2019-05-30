---
title: DEBUG_CUSTOM_VIEWER | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2ba4af7ef465a4d98f78eccc9f7dce7dd4fa43aa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346196"
---
# <a name="debugcustomviewer"></a>DEBUG_CUSTOM_VIEWER
Una estructura que identifica un visor personalizado o tipo de visualizador.

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
Un identificador para diferenciar varios visores o visualizadores implementados por una `GUID`.

`bstrMenuName`\
El texto que aparecerá en el menú desplegable.

`bstrDescription`\
Descripción del visor personalizado o visualizador de tipo (debe ser un valor null si no usa).

`guidLang`\
Idioma del evaluador de expresiones que proporcionan.

`guidVendor`\
Proveedor del evaluador de expresiones que proporcionan.

`bstrMetric`\
Métricas en la que el visor personalizado o un visualizador de tipo `CLSID` se almacena.

## <a name="remarks"></a>Comentarios
Se devuelve una lista de esta estructura mediante una llamada a la [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) método (y, por extensión, el [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) método).

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
