---
title: TYPE_INFO | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 610abe4bd01c47b09d6438508318e90a41f6802e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="typeinfo"></a>TYPE_INFO
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
  
#### <a name="parameters"></a>Parámetros  
 dwKind  
 Un valor de la [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) enumeración que determina cómo interpretar la unión.  
  
 type.typeMeta  
 [Solo en C++] Contiene un [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) estructura si `dwKind` es `TYPE_KIND_METADATA`.  
  
 type.typePdb  
 [Solo en C++] Contiene un [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) estructura si `dwKind` es `TYPE_KIND_PDB`.  
  
 type.typeBuilt  
 [Solo en C++] Contiene un [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) estructura si `dwKind` es `TYPE_KIND_BUILT`.  
  
 Type.Unused  
 Relleno sin usar.  
  
 type  
 Nombre de la unión.  
  
 UnionMember  
 [Sólo en C#] Calcular las referencias para el tipo de estructura adecuada según `dwKind`.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura se pasa a la [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) método donde se rellena. ¿Cómo se interpreta el contenido de la estructura se basa en el `dwKind` campo.  
  
> [!NOTE]
>  [Solo en C++] Si `dwKind` es igual a `TYPE_KIND_BUILT`, es necesario liberar subyacente [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto cuando se destruye el `TYPE_INFO` estructura. Esto se hace llamando a `typeInfo.type.typeBuilt.pUnderlyingField->Release()`.  
  
 [Sólo en C#] En la tabla siguiente se muestra cómo interpretar la `unionmember` miembro para cada clase de tipo. En el ejemplo se muestra cómo hacerlo para una clase de tipo.  
  
|`dwKind`|`unionmember` interpreta como|  
|--------------|----------------------------------|  
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|  
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|  
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo muestra cómo interpretar la `unionmember` miembro de la `TYPE_INFO` estructura en C#. Este ejemplo muestra la interpretación de un solo tipo (`TYPE_KIND_METADATA`), pero los demás se interpretan exactamente la misma manera.  
  
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
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)