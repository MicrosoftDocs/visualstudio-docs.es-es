---
title: "name (Propiedad, Error de JavaScript) | Microsoft Docs"
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
  - "name"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Name (propiedad)"
  - "name (propiedad), nombre de error"
ms.assetid: 94df2d6b-f1a1-4931-a956-0a930cb87f76
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# name (Propiedad, Error de JavaScript)
Devuelve el nombre de un error.  
  
## Sintaxis  
  
```  
  
errorObj.  
name  
  
```  
  
## Parámetros  
 `errorObj`  
 Obligatorio.  Instancia del objeto `Error`.  
  
## Comentarios  
 La propiedad **name** devuelve el nombre o el tipo de excepción de un error.  Cuando se produce un error en tiempo de ejecución, la propiedad name se establece en uno de los siguientes tipos de excepción nativos:  
  
|Tipo de excepción|Significado|  
|-----------------------|-----------------|  
|ConversionError|Este error se produce cuando se intenta convertir un objeto en algo en lo que no se puede convertir.|  
|RangeError|Este error se produce cuando se proporciona a una función un argumento que ha superado su intervalo permitido.  Por ejemplo, este error se produce si intentas construir un objeto `Array` con una longitud que no es un entero positivo válido.|  
|ReferenceError|Este error tiene lugar cuando se detecta una referencia no válida.  Por ejemplo, este error se producirá si una referencia que se espera es `null`.|  
|RegExpError|Este error se produce cuando tiene lugar un error de compilación con una expresión regular.  Sin embargo, una vez compilada la expresión regular, este error no se puede producir.  Por ejemplo, este error se producirá si se declara una expresión regular con un patrón cuya sintaxis no es válida, con marcas distintas de **i**, **g** o **m**, o si contiene la misma marca más de una vez.|  
|SyntaxError|Este error se produce cuando se analiza el texto de origen y su sintaxis no es correcta.  Por ejemplo, este error se producirá si se llama a la función `eval` con un argumento que no es un texto de programa válido.|  
|TypeError|Este error se produce cuando el tipo real de un operando no coincide con el tipo esperado.  Por ejemplo, este error se produce si se llama a una función sobre algo que no es un objeto o que no admite la llamada.|  
|URIError|Este error tiene lugar cuando se detecta un identificador uniforme de recursos \(URI\) no válido.  Por ejemplo, este error se producirá si se encuentra un carácter no válido en una cadena que se va a codificar o descodificar.|  
  
## Ejemplo  
 En el ejemplo siguiente se genera una excepción TypeError y se muestra el nombre del error y su mensaje.  
  
```javascript  
try  
{  
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
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Se aplica a**: [Error \(Objeto\)](../../javascript/reference/error-object-javascript.md)  
  
## Vea también  
 [description \(Propiedad, Error\)](../../javascript/reference/description-property-error-javascript.md)   
 [message \(Propiedad, Error\)](../../javascript/reference/message-property-error-javascript.md)   
 [number \(Propiedad, Error\)](../../javascript/reference/number-property-error-javascript.md)