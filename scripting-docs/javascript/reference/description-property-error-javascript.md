---
title: "description (Propiedad, Error de JavaScript) | Microsoft Docs"
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
  - "Description"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Description (propiedad)"
  - "control de errores, descripción del error"
  - "errores, description"
ms.assetid: ea727f1e-2041-4400-965c-67e6d47a1ff0
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# description (Propiedad, Error de JavaScript)
Devuelve o establece la cadena descriptiva asociada a un error específico.  
  
## Sintaxis  
  
```  
  
object  
.description [= stringExpression]  
```  
  
## Parámetros  
 *object*  
 Obligatorio.  Cualquier instancia de un objeto `Error`.  
  
 `stringExpression`  
 Opcional.  Expresión de cadena que contiene una descripción del error.  
  
## Comentarios  
 La propiedad **description** contiene la cadena de mensaje de error asociada a un error específico.  Usa el valor contenido en esta propiedad para avisar a un usuario de un error.  
  
 Las propiedades **description** y **message** proporcionan la misma funcionalidad; la propiedad **description** proporciona compatibilidad con versiones anteriores, mientras que la propiedad **message** cumple el estándar ECMA.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de la propiedad **description**.  
  
```javascript  
try  
{  
// Cause an error:  
    x = y     
}  
catch(e)  
{  
// Prints "[object Error]":  
    document.write(e)  
    document.write (" ");  
// Prints 5009:  
    document.write((e.number & 0xFFFF))    
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.description);  
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.message)  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Se aplica a**: [Error \(Objeto\)](../../javascript/reference/error-object-javascript.md)  
  
## Vea también  
 [number \(Propiedad, Error\)](../../javascript/reference/number-property-error-javascript.md)   
 [message \(Propiedad, Error\)](../../javascript/reference/message-property-error-javascript.md)   
 [name \(Propiedad, Error\)](../../javascript/reference/name-property-error-javascript.md)