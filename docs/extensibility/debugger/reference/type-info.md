---
title: TYPE_INFO Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 82796c1d82dc3ca77151abcec3e1dd6ce13ac59d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713329"
---
# <a name="type_info"></a>TYPE_INFO
Esta estructura especifica varios tipos de información sobre el tipo de un campo.

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

## <a name="members"></a>Miembros
 `dwKind`\
 Valor de la [enumeración dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) que determina cómo interpretar la unión.

 `type.typeMeta`\
 [Sólo C++] Contiene una estructura `dwKind` `TYPE_KIND_METADATA` [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) si es .

 `type.typePdb`\
 [Sólo C++] Contiene una estructura `dwKind` `TYPE_KIND_PDB` [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) si es .

 `type.typeBuilt`\
 [Sólo C++] Contiene una estructura `dwKind` `TYPE_KIND_BUILT` [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) si es .

 `type.unused`\
 Relleno no utilizado.

 `type`\
 Nombre del sindicato.

 `unionmember`\
 [Sólo C] Marshal esto para el tipo `dwKind`de estructura adecuado basado en .

## <a name="remarks"></a>Observaciones
 Esta estructura se pasa a la [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) método donde se rellena. La forma en que se interpreta el `dwKind` contenido de la estructura se basa en el campo.

> [!NOTE]
> [Sólo C++] Si `dwKind` es `TYPE_KIND_BUILT`igual, es necesario liberar el objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) `TYPE_INFO` subyacente al destruir la estructura. Esto se hace llamando a `typeInfo.type.typeBuilt.pUnderlyingField->Release()`.

 [Sólo C] En la tabla siguiente `unionmember` se muestra cómo interpretar el miembro para cada tipo de tipo. El ejemplo muestra cómo se hace esto para un tipo de tipo.

|`dwKind`|`unionmember`interpretado como|
|--------------|----------------------------------|
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|

## <a name="example"></a>Ejemplo
 En este ejemplo se `unionmember` muestra `TYPE_INFO` cómo interpretar el miembro de la estructura en C. En este ejemplo se muestra`TYPE_KIND_METADATA`la interpretación de solo un tipo ( ) pero los demás se interpretan exactamente de la misma manera.

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
 Encabezado: sh.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
