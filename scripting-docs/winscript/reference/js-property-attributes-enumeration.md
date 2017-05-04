---
title: "Enumeraci&#243;n JS_PROPERTY_ATTRIBUTES | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JS_PROPERTY_ATTRIBUTES
apilocation: jscript9diag.dll
ms.assetid: e83b9b6c-5b21-48d1-92b6-22bed926b18b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Enumeraci&#243;n JS_PROPERTY_ATTRIBUTES
Indica los atributos de una propiedad.  
  
## Sintaxis  
  
```  
enum JS_PROPERTY_ATTRIBUTES  
{  
   JS_PROPERTY_ATTRIBUTE_NONE = 0,  
   JS_PROPERTY_HAS_CHILDREN = 0x1,  
   JS_PROPERTY_FAKE = 0x2,  
   JS_PROPERTY_METHOD = 0x4,  
   JS_PROPERTY_READONLY = 0x8,  
   JS_PROPERTY_NATIVE_WINRT_POINTER = 0x10  
} JS_PROPERTY_ATTRIBUTES;  
```  
  
## Miembros  
  
|Nombre|Descripción|  
|------------|-----------------|  
|`JS_PROPERTY_ATTRIBUTE_NONE`|La propiedad no tiene atributos.|  
|`JS_PROPERTY_HAS_CHILDREN`|La propiedad tiene elementos secundarios.|  
|`JS_PROPERTY_FAKE`|La propiedad representa un nodo ficticio, como "\[Métodos\]".|  
|`JS_PROPERTY_METHOD`|La propiedad es un método.|  
|`JS_PROPERTY_READONLY`|La propiedad es de solo lectura.|  
|`JS_PROPERTY_NATIVE_WINRT_POINTER`|La propiedad es un puntero a un objeto nativo de WinRT.|  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)