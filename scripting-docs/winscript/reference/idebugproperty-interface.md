---
title: "IDebugProperty (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugProperty (interfaz)"
ms.assetid: 7e8f5341-23ef-4029-814d-f5c2307b9203
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty (Interfaz)
Se utiliza para describir las propiedades jerárquica de la entidad que se depure que tiene un nombre, tipo, y un valor.  Normalmente, `IDebugProperty` se utiliza para describir el resultado de la evaluación de la expresión, la evaluación de extraer, o la evaluación del registro.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de la interfaz de `IDebugProperty` .  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugProperty::GetPropertyInfo](../../winscript/reference/idebugproperty-getpropertyinfo.md)|Obtiene `DebugPropertyInfo` que describe este `IDebugProperty``.`|  
|[IDebugProperty::GetExtendedInfo](../../winscript/reference/idebugproperty-getextendedinfo.md)|Obtiene información extendida en una propiedad.|  
|[IDebugProperty::SetValueAsString](../../winscript/reference/idebugproperty-setvalueasstring.md)|establece el valor de una propiedad de una cadena.|  
|[IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)|Muestra los miembros de una propiedad.|  
|[IDebugProperty::GetParent](../../winscript/reference/idebugproperty-getparent.md)|Obtiene el elemento primario de una propiedad.|  
  
## Requisitos  
 Encabezado: dbgprop.h