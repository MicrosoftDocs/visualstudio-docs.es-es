---
title: "ADDRESS_KIND | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ADDRESS_KIND"
helpviewer_keywords: 
  - "Enumeración ADDRESS_KIND"
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# ADDRESS_KIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

especifica las clases de direcciones.  
  
## Sintaxis  
  
```cpp  
enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
typedef DWORD ADDRESS_KIND;  
```  
  
```c#  
public enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
```  
  
## términos  
 ADDRESS\_KIND\_NATIVE  
 una dirección nativa, representada por la estructura de [NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md) .  
  
 ADDRESS\_KIND\_UNMANAGED\_THIS\_RELATIVE  
 Una dirección no administrada en relación con un puntero de `this` \(`Me` en Visual Basic\) y representada por la estructura de [UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) .  
  
 ADDRESS\_KIND\_UNMANAGED\_PHYSICAL  
 Una dirección física no administrada, representada por la estructura de [UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) .  
  
 ADDRESS\_KIND\_METHOD  
 un método de una clase, representado por la estructura de [METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) .  
  
 ADDRESS\_KIND\_FIELD  
 un campo de una clase, representado por la estructura de [METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) .  
  
 ADDRESS\_KIND\_LOCAL  
 La dirección es para una variable local y se representa mediante la estructura de [METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) .  
  
 ADDRESS\_KIND\_PARAM  
 Un parámetro del método o la función, representado por la estructura de [METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) .  
  
 ADDRESS\_KIND\_ARRAYELEM  
 un elemento de matriz, representado por la estructura de [METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) .  
  
 ADDRESS\_KIND\_RETVAL  
 un valor devuelto, representado por la estructura de [METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) .  
  
## Comentarios  
 el método de [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) devuelve la estructura que contiene una unión de estructuras posibles, la estructura de [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) de [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) .  El campo de `dwKind` de la estructura de `DEBUG_ADDRESS_UNION` contiene el valor de `ADDRESS_KIND` y describe cómo interpretar el campo de unión.  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)