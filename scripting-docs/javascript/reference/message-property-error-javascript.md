---
title: "message (Propiedad, Error de JavaScript) | Microsoft Docs"
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
  - "message"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Message (propiedad)"
ms.assetid: 8cab0392-e0db-4714-827c-47ab04e8b4f2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# message (Propiedad, Error de JavaScript)
Devuelve una cadena con un mensaje de error.  
  
## Sintaxis  
  
```  
  
errorObj.message  
```  
  
## Parámetros  
 `errorObj`  
 Obligatorio.  Instancia del objeto `Error`.  
  
## Comentarios  
 La propiedad `message` devuelve una cadena que contiene un mensaje de error asociado a un error específico.  
  
 Las propiedades `description` y `message` proporcionan la misma funcionalidad.  La propiedad `description` proporciona compatibilidad con versiones anteriores; la propiedad `message` cumple el estándar ECMA.  
  
## Ejemplo  
 En el ejemplo siguiente se genera una excepción TypeError y se muestra el nombre del error y su mensaje.  
  
```javascript  
try  
{  
    // Cause an error.  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## Ejemplo  
 El resultado de este código es el siguiente.  
  
```javascript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Se aplica a**: [Error \(Objeto\)](../../javascript/reference/error-object-javascript.md)  
  
## Vea también  
 [description \(Propiedad, Error\)](../../javascript/reference/description-property-error-javascript.md)   
 [name \(Propiedad, Error\)](../../javascript/reference/name-property-error-javascript.md)