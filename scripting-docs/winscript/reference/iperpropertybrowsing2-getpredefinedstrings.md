---
title: "IPerPropertyBrowsing2::GetPredefinedStrings | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.GetPredefinedStrings
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::GetPredefinedStrings"
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::GetPredefinedStrings
Permite que el llamador rellenar un cuadro de lista con una matriz contado de punteros de cadenas que representan valores posibles para esta propiedad.  
  
## Sintaxis  
  
```  
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### Parámetros  
 `dispid`  
 \[in\] identificador de envío de la propiedad para la que el llamador se soliciten la lista de la cadena.  
  
 `pCaStrings`  
 \[out\] puntero a una estructura asignados por el llamador, contada array que contiene el número de elementos y la dirección de una matriz método\- asignado de punteros de la cadena.  Si el método, no se asigna ningún memoria, y el contenido de la estructura son indefinidos.  
  
 `pCaCookies`  
 \[out\] puntero a la estructura asignados por el llamador, contada array que contiene el número de elementos y la dirección de una matriz método\- asignado de DWORD.  Si el método, no se asigna ningún memoria, y el contenido de la estructura son indefinidos.  
  
## Valor devuelto  
 Devuelve `HRESULT`válido, normalmente `S_OK`.  
  
## Vea también  
 [IPerPropertyBrowsing2 \(Interfaz\)](../../winscript/reference/iperpropertybrowsing2-interface-1.md)