---
title: "IEnumDebugPropertyInfo::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugPropertyInfo.Next
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo::Next"
ms.assetid: 052837ac-1599-49cc-9a5a-ba90f992eeff
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugPropertyInfo::Next
Recupera un número especificado de estructuras de `DebugPropertyInfo` en una secuencia de enumeración.  
  
## Sintaxis  
  
```  
HRESULT Next (  
   ULONG celt,  
   DebugPropertyInfo*rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### Parámetros  
 `celt`  
 \[in\] número de estructurasde `DebugPropertyInfo`que se recuperarán.  
  
 `rgelt`  
 \[out\] matriz de estructuras de `DebugPropertyInfo` recuperadas.  
  
 `pceltFetched`  
 \[out\] devuelve el número de estructuras de `DebugPropertyInfo` recuperadas realmente.  
  
## Valor devuelto  
 Devuelve `HRESULT`válido, normalmente `S_OK`.  
  
## Vea también  
 [IEnumDebugPropertyInfo \(Interfaz\)](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [DebugPropertyInfo \(Estructura\)](../../winscript/reference/debugpropertyinfo-structure.md)