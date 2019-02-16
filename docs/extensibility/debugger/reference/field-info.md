---
title: FIELD_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b34624672b64d88ca9b080094c5d661494c089cf
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315903"
---
# <a name="fieldinfo"></a>FIELD_INFO
Esta estructura describe otro campo, parámetro o una variable local.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct _tagFieldInfo {
    FIELD_INFO_FIELDS dwFields;
    BSTR              bstrFullName;
    BSTR              bstrName;
    BSTR              bstrType;
    FIELD_MODIFIERS   dwModifiers;
} FIELD_INFO;
```

```csharp
public struct FIELD_INFO {
    public uint   dwFields;
    public string bstrFullName;
    public string bstrName;
    public string bstrType;
    public uint   dwModifiers;
};
```

## <a name="members"></a>Miembros
dwFields  
Una combinación de marcas de la [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) enumeración que especifica qué miembros se rellenan.

bstrFullName  
El nombre completo del campo.

bstrName  
El nombre corto del campo.

bstrType  
El tipo del campo.

dwModifiers  
Una combinación de marcas de la [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) enumeración que describe el campo.

## <a name="remarks"></a>Comentarios
Esta estructura se pasa a la [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) método donde se rellena.

## <a name="requirements"></a>Requisitos
Encabezado: sh.h

Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
[Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)  
[FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)  
[FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)  
[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
