---
title: DEBUG_REFERENCE_INFO Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e31205f52151679f932877c9c4fdc56907ea59e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737417"
---
# <a name="debug_reference_info"></a>DEBUG_REFERENCE_INFO
Describe una referencia.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct tagDEBUG_REFERENCE_INFO {
    DEBUGREF_INFO_FLAGS dwFields;
    BSTR                bstrName;
    BSTR                bstrType;
    BSTR                bstrValue;
    DBG_ATTRIB_FLAGS    dwAttrib;
    REFERENCE_TYPE.     dwRefType;
    IDebugReference2*   m_pReference;
} DEBUG_REFERENCE_INFO;
```

```csharp
public struct DEBUG_REFERENCE_INFO {
    public uint             dwFields;
    public string           bstrName;
    public string           bstrType;
    public string           bstrValue;
    public ulong            dwAttrib;
    public uint.            dwRefType;
    public IDebugReference2 m_pReference;
};
```

## <a name="members"></a>Miembros
`dwFields`\
Una combinación de indicadores de la [enumeración DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) que especifica qué campos se rellenan.

`bstrName`\
El nombre especificado por el usuario del objeto [IDebugReference2.](../../../extensibility/debugger/reference/idebugreference2.md)

`bstrType`\
El tipo de referencia como una cadena con formato.

`bstrValue`\
El valor de referencia como una cadena formateada

`dwAttrib`\
Una combinación de indicadores de la [enumeración DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) que especifica los indicadores para los atributos de propiedad de depuración.

`dwRefType`\
Valor de la [enumeración REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) que especifica si el tipo de referencia es seguro o débil.

`m_pReference`\
Un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objeto que especifica la información de referencia.

## <a name="remarks"></a>Observaciones
Esta estructura se pasa a una llamada a la [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) método que se va a rellenar. Esta estructura también se devuelve como parte de una lista de la [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) interfaz que, a su vez, se devuelve de una llamada a la [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) método.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
