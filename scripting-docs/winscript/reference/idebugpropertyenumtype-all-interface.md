---
title: "IDebugPropertyEnumType_All (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugPropertyEnumType_All
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugPropertyEnumType_All (interfaz)"
ms.assetid: 4d0f4fd5-e5f7-47cb-b746-860d6363e2cd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPropertyEnumType_All (Interfaz)
Se definen las interfaces de `IDebugPropertyEnumType` para poder pasar cada uno de sus los identificadores IID como filtro de `IDebugProperty::EnumMembers` mientras solicite el enumerador adecuado.  
  
## Sintaxis  
  
```  
IDebugPropertyEnumType_All : IUnknown  
```  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugPropertyEnumType\_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|Devuelve una cadena de texto que describe el nombre|  
  
 Las interfaces siguientes heredan de `IDebugPropertyEnumType_All`, y no tienen ningún método adicional.  
  
```  
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## Vea también  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)