---
title: "IEnumDebugExtendedPropertyInfo::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExtendedPropertyInfo.Next
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugExtendedPropertyInfo::Next"
ms.assetid: ac41c9a3-19d1-4596-8a87-01c10b131be3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExtendedPropertyInfo::Next
Recupera un númeroespecificado de estructuras de`ExtendedDebugPropertyInfo` en una secuencia de enumeración.  
  
## Sintaxis  
  
```  
HRESULT Next (  
   ULONG celt,  
   ExtendedDebugPropertyInfo *rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### Parámetros  
 `celt`  
 \[in\] número de estructurasde `ExtendedDebugPropertyInfo`que se recuperarán.  
  
 `rgelt`  
 \[out\] matriz de estructuras de `ExtendedDebugPropertyInfo` recuperadas.  
  
 `pceltFetched`  
 \[out\] número de estructuras de `ExtendedDebugPropertyInfo` recuperadas realmente.  
  
## Valor devuelto  
 Devuelve `HRESULT`válido, normalmente `S_OK`.  
  
## Vea también  
 [IEnumDebugExtendedPropertyInfo \(Interfaz\)](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [ExtendedDebugPropertyInfo \(Estructura\)](../../winscript/reference/extendeddebugpropertyinfo-structure.md)