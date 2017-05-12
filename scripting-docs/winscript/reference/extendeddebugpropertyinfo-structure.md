---
title: "ExtendedDebugPropertyInfo (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ExtendedDebugPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "ExtendedDebugPropertyInfo (estructura)"
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ExtendedDebugPropertyInfo (Estructura)
Extiende la estructura de `DebugPropertyInfo` con miembros adicionales para caracterizar la propiedad extendida.  
  
## Sintaxis  
  
```  
typedef struct ExtendedDebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   LPOLESTR  bstrName;  
   LPOLESTR  bstrType;  
   LPOLESTR  bstrValue;  
   LPOLESTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
   DWORD  nDISPID;  
   DWORD  nType;  
   VARIANT  varValue;  
   ILockBytes*  plbValue;  
   IDebugExtendedProperty*  pDebugExtProp;  
};  
```  
  
## Members  
 `dwValidFields`  
 Un tipo de datos enumerado utilizado para especificar se inicializan los campos.  
  
 `bstrName`  
 El nombre de propiedad en un contexto.  
  
 `bstrType`  
 El tipo de propiedad como una cadena con formato.  
  
 `bstrValue`  
 El valor de propiedad como una cadena con formato.  
  
 `bstrFullName`  
 el nombre completo de la propiedad.  
  
 `dwAttrib`  
 Una enumeración que especifica los marcadores de la propiedad de depuración admite.  
  
 `pDebugProp`  
 Objeto de`IDebugProperty` correspondiente a este `ExtendedDebugPropertyInfo`.  
  
 `nDISPID`  
 El identificador de envío  
  
 `nType`  
 El tipo de propiedad extendida.  
  
 `varValue`  
 El valor de propiedad extendida si puede ajustarse a VARIANT.  
  
 `plbValue`  
 Bytes de datos reales del valor de propiedad.  
  
 `pDebugExtProp`  
 Objeto de`IDebugExtendedProperty` correspondiente a este `ExtendedDebugPropertyInfo`.  
  
## Vea también  
 [DebugPropertyInfo \(Estructura\)](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty \(Interfaz\)](../../winscript/reference/idebugproperty-interface.md)   
 [IDebugExtendedProperty \(Interfaz\)](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP\_ATTRIB\_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)