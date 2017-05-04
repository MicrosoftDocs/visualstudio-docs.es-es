---
title: "DBGPROP_INFO_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DBGPROP_INFO_FLAGS
apilocation: scrobj.dll
f1_keywords: 
  - "DBGPROP_INFO_FLAGS"
helpviewer_keywords: 
  - "DBGPROP_INFO_FLAGS"
ms.assetid: e9450a21-a802-4c3e-8b3d-8e202f555de1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DBGPROP_INFO_FLAGS
Se utiliza para especificar los campos de `DebugPropertyInfo`  
  
## Sintaxis  
  
```  
enum {  
   DBGPROP_INFO_NAME  =0x001,  
   DBGPROP_INFO_TYPE  =0x002,  
   DBGPROP_INFO_VALUE  =0x004,  
   DBGPROP_INFO_FULLNAME  =0x020,  
   DBGPROP_INFO_ATTRIBUTES  =0x008,  
   DBGPROP_INFO_DEBUGPROP  =0x010,  
   DBGPROP_INFO_AUTOEXPAND  =0x8000000  
};  
```  
  
## Members  
 DBGPROP\_INFORMATION\_NAME  
 Inicializa el campo de `bstrName` .  
  
 DBGPROP\_INFORMATION\_TYPE  
 Inicializa el campo de `bstrType` .  
  
 DBGPROP\_INFORMATION\_VALUE  
 Inicializa el campo de `bstrValue` .  
  
 DBGPROP\_INFORMATION\_FULLNAME  
 Inicializa el campo de `bstrFullName` .  
  
 DBGPROP\_INFORMATION\_ATTRIBUTES  
 Inicializa el campo de `dwAttrib` .  
  
 DBGPROP\_INFORMATION\_DEBUGPROP  
 Inicializa el campo de `pDebugProp` que contiene una interfaz de `IDebugProperty` .  
  
 DBGPROP\_INFORMATION\_AUTOEXPAND  
 Especifica que el campo value debe contener el valor auto\-expandido, si está disponible, para este tipo de objeto.  
  
## Vea también  
 [DebugPropertyInfo \(Estructura\)](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty \(Interfaz\)](../../winscript/reference/idebugproperty-interface.md)