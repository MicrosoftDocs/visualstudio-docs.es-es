---
title: TYPE_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 12102c297c34649c753cf1c811994f9e750b9605
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2020
ms.locfileid: "91838485"
---
# <a name="type_info"></a>TYPE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta estructura especifica diversos tipos de información sobre el tipo de un campo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 Un valor de la enumeración [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) que determina cómo interpretar la Unión.  
  
 Escriba. typeMeta  
 [Solo C++] Contiene una estructura de [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) si `dwKind` es `TYPE_KIND_METADATA` .  
  
 Escriba. typePdb  
 [Solo C++] Contiene una estructura de [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) si `dwKind` es `TYPE_KIND_PDB` .  
  
 Escriba. typeBuilt  
 [Solo C++] Contiene una estructura de [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) si `dwKind` es `TYPE_KIND_BUILT` .  
  
 tipo. sin usar  
 Relleno sin usar.  
  
 type  
 Nombre de la Unión.  
  
 unionmember  
 [Solo C#] Calcular las referencias de este en el tipo de estructura adecuado basado en `dwKind` .  
  
## <a name="remarks"></a>Observaciones  
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
  
## <a name="see-also"></a>Consulte también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
