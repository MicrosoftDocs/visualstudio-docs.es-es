---
title: "IPerPropertyBrowsing2::SetPredefinedValue | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.SetPredefinedValue
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::SetPredefinedValue"
ms.assetid: 3aff5300-c5a4-4d9b-9d47-a75b64014ac4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::SetPredefinedValue
Establece el valor de la propiedad especificada por `dispID`.  El valor predefinido se identifica mediante el token `dwCookie.`  
  
## Sintaxis  
  
```  
HRESULT SetPredefinedValue(  
   DISPID  dispid,  
   DWORD  dwCookie  
);  
```  
  
#### Parámetros  
 `dispid`  
 \[in\] identificador de envío de la propiedad que se está estableciendo un valor predefinido.  
  
 `dwCookie`  
 \[in\] token que identifica el valor al conjunto.  
  
## Valor devuelto  
 Devuelve `HRESULT`válido, normalmente `S_OK`.  
  
## Vea también  
 [IPerPropertyBrowsing2 \(Interfaz\)](../../winscript/reference/iperpropertybrowsing2-interface-1.md)