---
title: "IEnumDebugExtendedPropertyInfo::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExtendedPropertyInfo.Skip
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugExtendedPropertyInfo::Skip"
ms.assetid: a0b4a9fc-e122-482b-9384-b83c460b61fe
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExtendedPropertyInfo::Skip
Omite un número especificado de estructuras de `ExtendedDebugPropertyInfo` en una secuencia de enumeración.  
  
## Sintaxis  
  
```  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### Parámetros  
 `celt`  
 \[in\] número de estructuras de `ExtendedDebugPropertyInfo` en la secuencia de enumeración al salto.  
  
## Valor devuelto  
 Devuelve `HRESULT`válido, normalmente `S_OK`.  Devuelve `S_FALSE` y establece el puntero de elemento actual al final de la enumeración si `celt` es mayor que el número de elementos que quedan en el enumerador.  
  
## Vea también  
 [IEnumDebugExtendedPropertyInfo \(Interfaz\)](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [ExtendedDebugPropertyInfo \(Estructura\)](../../winscript/reference/extendeddebugpropertyinfo-structure.md)