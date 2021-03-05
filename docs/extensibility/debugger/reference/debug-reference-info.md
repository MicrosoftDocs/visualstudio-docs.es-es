---
description: Describe una referencia de.
title: DEBUG_REFERENCE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e210875f88a7c8246eff3bfcf0721d6866602b7e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170541"
---
# <a name="debug_reference_info"></a>DEBUG_REFERENCE_INFO
Describe una referencia de.

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

## <a name="members"></a>Members
`dwFields`\
Combinación de marcas de la enumeración [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) que especifica qué campos se rellenan.

`bstrName`\
Nombre especificado por el usuario del objeto [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) .

`bstrType`\
El tipo de referencia como una cadena con formato.

`bstrValue`\
El valor de referencia como una cadena con formato

`dwAttrib`\
Combinación de marcas de la enumeración [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) que especifica las marcas de los atributos de la propiedad Debug.

`dwRefType`\
Un valor de la enumeración [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) que especifica si el tipo de referencia es fuerte o débil.

`m_pReference`\
Objeto [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) que especifica la información de referencia.

## <a name="remarks"></a>Observaciones
Esta estructura se pasa a una llamada al método [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) que se va a rellenar. Esta estructura también se devuelve como parte de una lista de la interfaz [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) que, a su vez, se devuelve desde una llamada al método [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) .

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
