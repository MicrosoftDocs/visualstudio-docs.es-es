---
title: "IDebugProperty::GetPropertyInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.GetPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::GetPropertyInfo"
ms.assetid: b201c0c4-bff6-4285-880f-67be90584c5f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::GetPropertyInfo
Obtiene el valor de `IDebugProperty` que describe un método o una propiedad indizada.  
  
## Sintaxis  
  
```  
HRESULT GetPropertyInfo (  
   DBGPROP_INFO_FLAGS dwFields,  
   UINT nRadix,  
   DebugPropertyInfo* pPropertyInfo  
);  
```  
  
#### Parámetros  
 `dwFields`  
 \[in\] especifica las constantes de `DBGPROP_INFO_FLAGS` que determinan los campos que se completan comentario la estructura de `DebugPropertyInfo` .  
  
 `nRadix`  
 \[in\]  Base que se utilizará para dar formato a cualquier información numérica.  
  
 `pPropertyInfo`  
 \[out\] devuelve la estructura de `DebugPropertyInfo` que describe la propiedad.  
  
## Valor devuelto  
 Devuelve `HRESULT`válido, normalmente `S_OK`.  
  
## Vea también  
 [IDebugProperty \(Interfaz\)](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [DebugPropertyInfo \(Estructura\)](../../winscript/reference/debugpropertyinfo-structure.md)