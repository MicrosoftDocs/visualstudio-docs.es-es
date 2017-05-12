---
title: "IDebugExtendedProperty::GetExtendedPropertyInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExtendedProperty.GetExtendedPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugExtendedProperty::GetExtendedPropertyInfo"
ms.assetid: 56edf538-5082-4653-82b6-e6640d6f61ba
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExtendedProperty::GetExtendedPropertyInfo
Captura información extendida para una propiedad extendida, que es más información que `IDebugProperty`más simple.  
  
## Sintaxis  
  
```  
HRESULT GetExtendedPropertyInfo(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   ExtendedDebugPropertyInfo*  pExtendedPropertyInfo  
);  
```  
  
#### Parámetros  
 `dwFieldSpec`  
 \[in\] especifica las constantes de EX\_DBGPROP\_INFO\_FLAGS que determinan los campos que se completan comentario la estructura de `ExtendedDebugPropertyInfo` .  
  
 `nRadix`  
 \[in\] base que se utilizará en la interpretación de cualquier información numérica.  
  
 `pExtendedPropertyInfo`  
 \[out\] devuelve la estructura de `ExtendedDebugPropertyInfo` que describe la propiedad.  
  
## Valor devuelto  
 Devuelve `HRESULT`válido, normalmente `S_OK`.  
  
## Vea también  
 [IDebugExtendedProperty \(Interfaz\)](../../winscript/reference/idebugextendedproperty-interface.md)   
 [EX\_DBGPROP\_INFO\_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)   
 [ExtendedDebugPropertyInfo \(Estructura\)](../../winscript/reference/extendeddebugpropertyinfo-structure.md)