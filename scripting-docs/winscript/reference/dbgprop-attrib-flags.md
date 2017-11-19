---
title: DBGPROP_ATTRIB_FLAGS | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DBGPROP_ATTRIB_FLAGS
apilocation: scrobj.dll
f1_keywords: DBGPROP_ATTRIB_FLAGS
helpviewer_keywords: DBGPROP_ATTRIB_FLAGS
ms.assetid: 90314496-527b-4357-9df8-125a360bf216
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 43db6cd118e2097d857d5c41334341c595088302
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="dbgpropattribflags"></a>DBGPROP_ATTRIB_FLAGS
Describe los distintos atributos de `IDebugProperty`. Miembro de la estructura `DebugPropertyInfo`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
enum {  
DBGPROP_ATTRIB_NO_ATTRIB  =0x00000000,  
   DBGPROP_ATTRIB_VALUE_IS_INVALID  =0x00000008,  
   DBGPROP_ATTRIB_VALUE_IS_EXPANDABLE  =0x00000010,  
   DBGPROP_ATTRIB_VALUE_READONLY  =0x00000800,  
   DBGPROP_ATTRIB_ACCESS_PUBLIC  =0x00001000,  
   DBGPROP_ATTRIB_ACCESS_PRIVATE  =0x00002000,  
   DBGPROP_ATTRIB_ACCESS_PROTECTED  =0x00004000,  
   DBGPROP_ATTRIB_ACCESS_FINAL  =0x00008000,  
   DBGPROP_ATTRIB_STORAGE_GLOBAL  =0x00010000,  
   DBGPROP_ATTRIB_STORAGE_STATIC  =0x00020000,  
   DBGPROP_ATTRIB_STORAGE_FIELD  =0x00040000,  
   DBGPROP_ATTRIB_STORAGE_VIRTUAL  =0x00080000,  
   DBGPROP_ATTRIB_TYPE_IS_CONSTANT  =0x00100000,  
   DBGPROP_ATTRIB_TYPE_IS_SYNCHRONIZED  =0x00200000,  
   DBGPROP_ATTRIB_TYPE_IS_VOLATILE  =0x00400000,  
   DBGPROP_ATTRIB_HAS_EXTENDED_ATTRIBS  =0x00800000  
   DBGPROP_ATTRIB_VALUE_IS_RETURN_VALUE  =0x08000000,  
};  
  
```  
  
## <a name="members"></a>Miembros  
 DBGPROP_ATTRIB_NO_ATTRIB  
 Indica que no hay atributos.  
  
 DBGPROP_ATTRIB_VALUE_IS_INVALID  
 Indica que el valor de `DebugPropertyInfo::bstrValue` no es válido.  
  
 DBGPROP_ATTRIB_VALUE_IS_EXPANDABLE  
 Indica que la propiedad o referencia tiene elementos secundarios.  
  
 DBGPROP_ATTRIB_VALUE_READONLY  
 Indica que el valor es de solo lectura.  
  
 DBGPROP_ATTRIB_ACCESS_PUBLIC  
 Indica un objeto que tiene acceso público.  
  
 DBGPROP_ATTRIB_ACCESS_PRIVATE  
 Indica un objeto que tiene acceso privado.  
  
 DBGPROP_ATTRIB_ACCESS_PROTECTED  
 Indica un objeto que tiene acceso protegido.  
  
 DBGPROP_ATTRIB_ACCESS_FINAL  
 Indica un objeto que tiene acceso final.  
  
 DBGPROP_ATTRIB_STORAGE_GLOBAL  
 Indica almacenamiento global.  
  
 DBGPROP_ATTRIB_STORAGE_STATIC  
 Indica almacenamiento estático.  
  
 DBGPROP_ATTRIB_STORAGE_FIELD  
 Indica un objeto que es una propiedad.  
  
 DBGPROP_ATTRIB_STORAGE_VIRTUAL  
 Indica almacenamiento virtual.  
  
 DBGPROP_ATTRIB_TYPE_IS_CONSTANT  
 Indica que el tipo de objeto es constante.  
  
 DBGPROP_ATTRIB_TYPE_IS_SYNCHRONIZED  
 Indica que esta ranura está sincronizada con subprocesos.  
  
 DBGPROP_ATTRIB_TYPE_IS_VOLATILE  
 Indica que esta ranura es volátil con respecto al almacenamiento persistente.  
  
 DBGPROP_ATTRIB_HAS_EXTENDED_ATTRIBS  
 Indica que esta ranura tiene atributos más allá de estos bits predefinidos.  
  
 DBGPROP_ATTRIB_VALUE_IS_RETURN_VALUE  
 Indica que el valor es un valor devuelto de una función.  
  
## <a name="remarks"></a>Comentarios  
 Estas marcas también se usan para filtrar los elementos secundarios de un objeto. Los valores pueden combinarse con una operación OR bit a bit.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProperty (interfaz)](../../winscript/reference/idebugproperty-interface.md)   
 [DebugPropertyInfo (Estructura)](../../winscript/reference/debugpropertyinfo-structure.md)