---
title: "TYPE_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TYPE_INFO"
helpviewer_keywords: 
  - "Estructura TYPE_INFO"
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# TYPE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta estructura especifica a distintos tipos de información sobre un tipo de campo.  
  
## Sintaxis  
  
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
  
```c#  
public struct TYPE_INFO {  
   public uint   dwKind;  
   public IntPtr unionmember;  
};  
```  
  
#### Parámetros  
 dwKind  
 Un valor de enumeración de [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) que determina cómo interpretar la combinación.  
  
 type.typeMeta  
 \[C\+\+\] sólo Contiene una estructura de [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md) si `dwKind` es `TYPE_KIND_METADATA`.  
  
 type.typePdb  
 \[C\+\+\] sólo Contiene una estructura de [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md) si `dwKind` es `TYPE_KIND_PDB`.  
  
 type.typeBuilt  
 \[C\+\+\] sólo Contiene una estructura de [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md) si `dwKind` es `TYPE_KIND_BUILT`.  
  
 type.unused  
 Relleno no.  
  
 type  
 nombre de la unión.  
  
 unionmember  
 \[C\# solo\] forma esto al tipo adecuado de la estructura basado en `dwKind`.  
  
## Comentarios  
 Esta estructura se pasa al método de [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) donde se completa.  Cómo el contenido de la estructura se interpretan se basa en el campo de `dwKind` .  
  
> [!NOTE]
>  \[C\+\+\] sólo si `dwKind` es igual a `TYPE_KIND_BUILT`, es necesario liberar el objeto subyacente de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) el destruir la estructura de `TYPE_INFO` .  Esto se hace llamando a `typeInfo.type.typeBuilt.pUnderlyingField->Release()`.  
  
 \[C\# solo\] en la tabla siguiente se muestra cómo interpretar el miembro de `unionmember` para cada clase de tipo.  El ejemplo muestra cómo esto se realiza para una clase de tipo.  
  
|`dwKind`|`unionmember` ha interpretado como|  
|--------------|----------------------------------------|  
|`TYPE_KIND_METADATA`|[METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|  
|`TYPE_KIND_PDB`|[PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|  
|`TYPE_KIND_BUILT`|[BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)|  
  
## Ejemplo  
 Este ejemplo muestra cómo interpretar el miembro de `unionmember` de la estructura de `TYPE_INFO` en C\#.  Este ejemplo muestra la interpretación de sólo un tipo \(`TYPE_KIND_METADATA`\) pero los otros se interpretan de la misma manera.  
  
```c#  
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
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)