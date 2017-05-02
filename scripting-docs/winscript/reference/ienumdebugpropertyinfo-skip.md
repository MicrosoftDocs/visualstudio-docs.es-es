---
title: "IEnumDebugPropertyInfo::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugPropertyInfo.Skip
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo::Skip"
ms.assetid: 2f6361fb-d66d-4fc0-8fe0-c859593a183f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugPropertyInfo::Skip
Omite un número especificado de estructuras de `DebugPropertyInfo` en una secuencia de enumeración.  
  
## Sintaxis  
  
```  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### Parámetros  
 `celt`  
 \[in\] número de estructuras de `DebugPropertyInfo` en la secuencia de enumeración al salto.  
  
## Valor devuelto  
 Devuelve `HRESULT`válido, normalmente `S_OK`.  Devuelve `S_FALSE` y establece el puntero de elemento actual al final de la enumeración si `celt` es mayor que el número de elementos que quedan en el enumerador.  
  
## Vea también  
 [IEnumDebugPropertyInfo \(Interfaz\)](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [DebugPropertyInfo \(Estructura\)](../../winscript/reference/debugpropertyinfo-structure.md)