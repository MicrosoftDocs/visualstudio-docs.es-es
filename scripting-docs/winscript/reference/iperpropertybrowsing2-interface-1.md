---
title: "IPerPropertyBrowsing2 (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2 (interfaz)"
ms.assetid: 1e50b3f7-cc1c-495a-93c7-3ee03aea0b8a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IPerPropertyBrowsing2 (Interfaz)
Tiene acceso a la información en las páginas de propiedades proporcionadas por un objeto.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|`GetDisplayString`|Devuelve una cadena de texto que describe la propiedad especificada.|  
|`MapPropertyToPage`|Devuelve el CLSID de la página de propiedades que permite la manipulación de la propiedad especificada.|  
|`GetPredefinedStrings`|Devuelve una matriz contado de cadenas \(punteros de`LPOLESTR` \) que enumeran las descripciones de los valores permitidos que la propiedad especificada puede aceptar.|  
|`SetPredefinedValue`|Establece el valor de la propiedad el valor predefinido identificado por el token `dwCookie.`|  
  
## Requisitos  
 Encabezado: dbgprop.h