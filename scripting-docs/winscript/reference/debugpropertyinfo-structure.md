---
title: "DebugPropertyInfo (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DebugPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DebugPropertyInfo (estructura)"
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DebugPropertyInfo (Estructura)
Describe un objeto de naturaleza jerárquica con nombre, el tipo, y valor.  Se utiliza para describir las propiedades de depuración de variables locales, parámetros, variables y expresiones de reloj, y registros.  
  
## Sintaxis  
  
```  
typedef struct DebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   BSTR  bstrName;  
   BSTR  bstrType;  
   BSTR  bstrValue;  
   BSTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
};  
```  
  
## Members  
 dwValidFields  
 Un tipo de datos enumerado utilizado para especificar se inicializan los campos.  
  
 bstrName  
 El nombre de propiedad en un contexto.  
  
 bstrType  
 El tipo de propiedad, como una cadena con formato.  
  
 bstrValue  
 El valor de propiedad, como una cadena con formato.  
  
 bstrFullName  
 el nombre completo de la propiedad.  
  
 dwAttrib  
 Una enumeración que especifica los marcadores de la propiedad de depuración admite.  
  
 pDebugProp  
 `IDebugProperty` descrito por la información de esta estructura de `DebugPropertyInfo` .  
  
## Vea también  
 [IDebugProperty \(Interfaz\)](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP\_ATTRIB\_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)