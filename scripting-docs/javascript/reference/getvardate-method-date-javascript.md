---
title: "getVarDate (M&#233;todo, Date de JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "getVarDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date (objeto)"
  - "getVarDate (método)"
  - "fechas, formato VT_DATE"
ms.assetid: 561238de-5c91-45a3-b839-a16910d3a1cf
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# getVarDate (M&#233;todo, Date de JavaScript)
Devuelve un valor VT\_DATE de un objeto `Date`.  
  
> [!WARNING]
>  Este método solo es válido en Internet Explorer.  
  
## Sintaxis  
  
```  
  
dateObj.getVarDate()   
```  
  
#### Parámetros  
 La referencia a `dateObj` necesaria es un objeto `Date`.  
  
## Valor devuelto  
 Devuelve un valor VT\_DATE.  
  
## Comentarios  
 El método `getVarDate` se usa cuando el código JavaScript interactúa con objetos COM, objetos ActiveX u otros objetos que aceptan y devuelven valores de fecha con el formato VT\_DATE. Entre estos se incluyen los objetos en Visual Basic y Visual Basic Scripting Edition \(VBScript\). El formato real del valor devuelto depende de la configuración regional.  
  
## Requisitos  
 Se admite en los siguientes modos de documento: Modo de interpretación, estándar de Internet Explorer 6, estándar de Internet Explorer 7, estándar de Internet Explorer 8, estándar de Internet Explorer 9 y estándar de Internet Explorer 10. No se admite en aplicaciones de [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Consulte [Información de versión](../../javascript/reference/javascript-version-information.md).  
  
 **Se aplica a**: [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [getDate \(Método, Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Date.parse \(Función\)](../../javascript/reference/date-parse-function-javascript.md)