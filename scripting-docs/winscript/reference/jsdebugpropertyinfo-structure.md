---
title: "Estructura JsDebugPropertyInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JsDebugPropertyInfo
apilocation: jscript9diag.dll
ms.assetid: 3a5463a7-2013-4846-9ab2-8beb675a5a6a
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Estructura JsDebugPropertyInfo
Indica información sobre una propiedad.  
  
## Sintaxis  
  
```  
typedef struct tagJsDebugPropertyInfo  
{  
   BSTR name;  
   BSTR type;  
   BSTR value;  
   BSTR fullName;  
   JS_PROPERTY_ATTRIBUTES attr;  
} JsDebugPropertyInfo;  
```  
  
## Miembros  
 `name`  
 Nombre de la propiedad.  
  
 `type`  
 Tipo de la propiedad.  
  
 `value`  
 El valor de la propiedad.  
  
 `fullName`  
 Nombre completo de la propiedad.  
  
 `attr`  
 Enumeración que representa los atributos de la propiedad.  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)