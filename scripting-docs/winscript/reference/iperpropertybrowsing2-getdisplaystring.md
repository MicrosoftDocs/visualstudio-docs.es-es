---
title: "IPerPropertyBrowsing2::GetDisplayString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.GetDisplayString
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::GetDisplayString"
ms.assetid: 8f75c6a9-86a9-4e2d-8cb4-74e7b1c0a524
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::GetDisplayString
Obtiene una cadena a los tipos que no son texto devuelto The inherentemente visible son un nombre que describe la propiedad y se pueden mostrar en la interfaz de usuario del llamador.  
  
## Sintaxis  
  
```  
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### Parámetros  
 `dispid`  
 \[in\] identificador de envío de la propiedad cuyo se solicita nombre para mostrar.  
  
 `pBstr`  
 \[out\] puntero a `BSTR` que contiene el nombre para mostrar de la propiedad identificada por `dispID`.  
  
## Valor devuelto  
 Devuelve `HRESULT`válido, normalmente `S_OK`.  
  
## Comentarios  
 La cadena devuelta no es un valor válido de la propiedad.  Trata simplemente de presentación de la cadena de la propiedad.  
  
## Vea también  
 [IPerPropertyBrowsing2 \(Interfaz\)](../../winscript/reference/iperpropertybrowsing2-interface-1.md)