---
title: "IPerPropertyBrowsing2::MapPropertyToPage | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.MapPropertyToPage
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::MapPropertyToPage"
ms.assetid: e6418a8e-500b-42e1-9b5a-52e6f7567f99
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::MapPropertyToPage
Devuelve el CLSID de la página de propiedades que se pueden utilizar para editar esta propiedad.  
  
## Sintaxis  
  
```  
HRESULT MapPropertyToPage(  
   DISPID  dispid,  
   CLSID*  pClsidPropPage  
);  
```  
  
#### Parámetros  
 `dispid`  
 \[in\] identificador de envío de la propiedad de interés.  
  
 `pClsidPropPage`  
 \[out\] el puntero al CLSID que identificaba la página de propiedades asociado a la propiedad.  Si se produce un error en este método, \*`pClsidPropPage` se establece en CLSID\_NULL.  
  
## Valor devuelto  
 Devuelve `HRESULT`válido, normalmente `S_OK`.  
  
## Vea también  
 [IPerPropertyBrowsing2 \(Interfaz\)](../../winscript/reference/iperpropertybrowsing2-interface-1.md)