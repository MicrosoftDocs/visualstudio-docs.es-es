---
title: "DEBUG_ADDRESS_UNION | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUG_ADDRESS_UNION"
helpviewer_keywords: 
  - "Unión DEBUG_ADDRESS_UNION"
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# DEBUG_ADDRESS_UNION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

describe diferentes tipos de direcciones.  
  
## Sintaxis  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS_UNION {  
   ADDRESS_KIND dwKind;  
   union {  
      NATIVE_ADDRESS                  addrNative;  
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;  
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;  
      METADATA_ADDRESS_METHOD         addrMethod;  
      METADATA_ADDRESS_FIELD          addrField;  
      METADATA_ADDRESS_LOCAL          addrLocal;  
      METADATA_ADDRESS_PARAM          addrParam;  
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;  
      METADATA_ADDRESS_RETVAL         addrRetVal;  
      DWORD                           unused;  
   } addr;  
} DEBUG_ADDRESS_UNION;  
```  
  
```c#  
public struct DEBUG_ADDRESS_UNION {  
   public ADDRESS_KIND dwKind;  
   public IntPtr       unionmember;  
}  
```  
  
## términos  
 dwKind  
 Un valor de enumeración de [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) , especificando cómo interpretar la combinación.  
  
 addr.addrNative  
 \[C\+\+ sólo\] Contiene la estructura de [NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md) si `dwKind` \= ADDRESS\_KIND\_NATIVE.  
  
 addr.addrThisRel  
 \[C\+\+ sólo\] Contiene la estructura de[UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) si `dwKind` \= ADDRESS\_KIND\_UNMANAGED\_THIS\_RELATIVE.  
  
 addr.addUPhysical  
 \[C\+\+ sólo\] Contiene la estructura de[UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) si `dwKind` \= ADDRESS\_KIND\_UNMANAGED\_PHYSICAL.  
  
 addr.addrMethod  
 \[C\+\+ sólo\] Contiene la estructura de[METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) si `dwKind` \= ADDRESS\_KIND\_METHOD.  
  
 addr.addrField  
 \[C\+\+ sólo\] Contiene la estructura de[METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) si `dwKind` \= ADDRESS\_KIND\_FIELD.  
  
 addr.addrLocal  
 \[C\+\+ sólo\] Contiene la estructura de[METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) si `dwKind` \= ADDRESS\_KIND\_LOCAL.  
  
 addr.addrParam  
 \[C\+\+ sólo\] Contiene la estructura de[METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) si `dwKind` \= ADDRESS\_KIND\_PARAM.  
  
 addr.addrArrayElem  
 \[C\+\+ sólo\] Contiene la estructura de[METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) si `dwKind` \= ADDRESS\_KIND\_ARRAYELEM.  
  
 addr.addrRetVal  
 \[C\+\+ sólo\] Contiene la estructura de[METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) si `dwKind` \= ADDRESS\_KIND\_RETVAL.  
  
 addr.unused  
 \[C\+\+ sólo\] finalizar el.  
  
 addr  
 \[C\+\+ sólo\] nombre de unión.  
  
 unionmember  
 \[C\#\] solo el valor de Esta tienen que calcularse al tipo adecuado de la estructura basado en `dwKind`.  Vea las notas de la asociación entre `dwKind` y la interpretación de unión.  
  
## Comentarios  
 Esta estructura es parte de la estructura de [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) y representa uno de varios tipos diferentes de direcciones \(la estructura de `DEBUG_ADDRESS` es completa por una llamada al método de [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) \).  
  
 \[C\# solo\] en la tabla siguiente se muestra cómo interpretar el miembro de `unionmember` para cada clase de dirección.  El ejemplo muestra cómo esto se realiza para una clase de dirección.  
  
|`dwKind`|`unionmember` ha interpretado como|  
|--------------|----------------------------------------|  
|`ADDRESS_KIND_NATIVE`|[NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|  
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|  
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|  
|`ADDRESS_KIND_METHOD`|[METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|  
|`ADDRESS_KIND_FIELD`|[METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|  
|`ADDRESS_KIND_LOCAL`|[METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|  
|`ADDRESS_KIND_PARAM`|[METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|  
|`ADDRESS_KIND_ARRAYELEM`|[METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|  
|`ADDRESS_KIND_RETVAL`|[METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|  
  
## Ejemplo  
 este ejemplo muestra cómo interpretar una clase de dirección \(`METADATA_ADDRESS_ARRAYELEM`\) de la estructura de `DEBUG_ADDRESS_UNION` en C\#.  los elementos restantes se pueden interpretar de la misma manera.  
  
```c#  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(DEBUG_ADDRESS_UNION dau)  
        {  
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)  
            {  
                 METADATA_ADDRESS_ARRAYELEM arrayElem =  
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,  
                                 typeof(METADATA_ADDRESS_ARRAYELEM));  
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
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)