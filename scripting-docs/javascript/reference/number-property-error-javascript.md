---
title: "number (Propiedad, Error de JavaScript) | Microsoft Docs"
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
  - "Number"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Number (propiedad)"
ms.assetid: 8697e20b-a2b0-4e26-85c0-ab07ddfe8281
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# number (Propiedad, Error de JavaScript)
Devuelve o establece el valor numérico asociado a un error específico.  La propiedad predeterminada del objeto `Error` es **number**.  
  
## Sintaxis  
  
```  
  
object  
.number [= errorNumber]  
```  
  
## Parámetros  
 *Object*  
 Cualquier instancia del objeto `Error`.  
  
 *errorNumber*  
 Entero que representa un error.  
  
## Comentarios  
 Un número de error es un valor de 32 bits.  La palabra de 16 bits superior es el código de facilidad, y la palabra inferior es el código de error.  Para determinar el código de error, usa el operador `&` \(AND bit a bit\) para agrupar la propiedad number con el número hexadecimal `0xFFFF`.  
  
## Ejemplo  
 En el ejemplo siguiente se produce una excepción y se muestra el código de error derivado del número de error.  
  
```javascript  
try  
    {  
    // Cause an error.  
    var x = y;  
    }  
catch(e)  
    {  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
  
    document.write ("Facility Code: ")  
    document.write(e.number>>16 & 0x1FFF)  
    document.write ("<br />");  
  
    document.write ("Error Message: ")  
    document.write (e.message)  
    }  
```  
  
## Ejemplo  
 El resultado de este código es el siguiente.  
  
```javascript  
Error Code: 5009  
Facility Code: 10  
Error Message: 'y' is undefined  
```  
  
## Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Se aplica a**: [Error \(Objeto\)](../../javascript/reference/error-object-javascript.md)  
  
## Vea también  
 [description \(Propiedad, Error\)](../../javascript/reference/description-property-error-javascript.md)   
 [message \(Propiedad, Error\)](../../javascript/reference/message-property-error-javascript.md)   
 [name \(Propiedad, Error\)](../../javascript/reference/name-property-error-javascript.md)