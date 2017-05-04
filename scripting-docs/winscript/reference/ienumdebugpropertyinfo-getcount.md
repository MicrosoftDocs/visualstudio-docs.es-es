---
title: "IEnumDebugPropertyInfo::GetCount | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugPropertyInfo.GetCount
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo::GetCount"
ms.assetid: 83a3becd-8533-4880-9c4f-193227ff25a9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugPropertyInfo::GetCount
Obtiene el número de estructuras de `DebugPropertyInfo` en el enumerador.  
  
## Sintaxis  
  
```  
HRESULT GetCount (  
   ULONG* pcelt  
);  
```  
  
#### Parámetros  
 `pcelt`  
 \[out\] devuelve el número de estructuras de `DebugPropertyInfo` en el enumerador.  
  
## Valor devuelto  
 Devuelve `HRESULT`válido, normalmente `S_OK`.  
  
## Vea también  
 [IEnumDebugPropertyInfo \(Interfaz\)](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [DebugPropertyInfo \(Estructura\)](../../winscript/reference/debugpropertyinfo-structure.md)