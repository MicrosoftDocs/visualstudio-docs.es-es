---
title: TYPE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eeb4a306e7b357c59f8d75a91e2c21c50f1ed16b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880091"
---
# <a name="type_info"></a>TYPE_INFO
Esta estructura especifica diversos tipos de información sobre el tipo de un campo.

## <a name="syntax"></a>Sintaxis

```cpp
struct _tagTYPE_INFO_UNION {
   dwTYPE_KIND dwKind;
   union {
      METADATA_TYPE typeMeta;
      PDB_TYPE      typePdb;
      BUILT_TYPE    typeBuilt;
      DWORD         unused;
   } type;
} TYPE_INFO;
```

```csharp
public struct TYPE_INFO {
   public uint   dwKind;
   public IntPtr unionmember;
};
```

## <a name="members"></a>Members
 `dwKind`\
 Un valor de la enumeración [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) que determina cómo interpretar la Unión.

 `type.typeMeta`\
 [Solo C++] Contiene una estructura de [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) si `dwKind` es `TYPE_KIND_METADATA` .

 `type.typePdb`\
 [Solo C++] Contiene una estructura de [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) si `dwKind` es `TYPE_KIND_PDB` .

 `type.typeBuilt`\
 [Solo C++] Contiene una estructura de [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) si `dwKind` es `TYPE_KIND_BUILT` .

 `type.unused`\
 Relleno sin usar.

 `type`\
 Nombre de la Unión.

 `unionmember`\
 [Solo C#] Calcular las referencias de este en el tipo de estructura adecuado basado en `dwKind` .

## <a name="remarks"></a>Notas
 Esta estructura se pasa al método [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) donde se rellena. El modo en que se interpreta el contenido de la estructura se basa en el `dwKind` campo.

> [!NOTE]
> [Solo C++] Si es `dwKind` igual `TYPE_KIND_BUILT` a, es necesario liberar el objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) subyacente al destruir la `TYPE_INFO` estructura. Esto se hace llamando a `typeInfo.type.typeBuilt.pUnderlyingField->Release()`.

 [Solo C#] En la tabla siguiente se muestra cómo interpretar el `unionmember` miembro para cada tipo de tipo. En el ejemplo se muestra cómo hacerlo para un tipo de.

|`dwKind`|`unionmember` se interpreta como|
|--------------|----------------------------------|
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|

## <a name="example"></a>Ejemplo
 En este ejemplo se muestra cómo interpretar el `unionmember` miembro de la `TYPE_INFO` estructura en C#. En este ejemplo se muestra la interpretación de un solo tipo ( `TYPE_KIND_METADATA` ), pero los demás se interpretan exactamente de la misma manera.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(TYPE_INFO ti)
        {
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)
            {
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,
                                               typeof(METADATA_TYPE));
            }
        }
    }
}
```

## <a name="requirements"></a>Requisitos
 Encabezado: SH. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
