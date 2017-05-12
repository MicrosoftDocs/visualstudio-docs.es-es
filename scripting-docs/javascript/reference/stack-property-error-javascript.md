---
title: "stack (Propiedad, Error de JavaScript) | Microsoft Docs"
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
  - "Error.stack"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "pila de errores [JavaScript]"
  - "pila de errores de JavaScript"
ms.assetid: 1dc21fdd-853c-4664-bf1c-24eb1f6f2daf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# stack (Propiedad, Error de JavaScript)
Obtiene o establece la pila de errores como una cadena que contiene los marcos del seguimiento de la pila.  
  
## Sintaxis  
  
```  
  
object  
.stack   
```  
  
## Comentarios  
 La propiedad `stack` se establece en `undefined` cuando se construye el error y obtiene la información de seguimiento cuando se produce el error.  Si un error se repite, la propiedad `stack` se actualiza cada vez que se produce el error.  
  
 Los marcos de pila se muestran en el formato siguiente: at NombreFunción \(\<Nombre completo\/URL\>:\<número de línea\>:\<número de columna\>\)  
  
 Si crea su propio objeto de error y establece el seguimiento de la pila en un valor, el valor no se sobrescribirá cuando se produzca el error.  
  
 La propiedad `stack` no muestra las funciones inline en sus marcos,  solo muestra la pila física.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo obtener la pila cuando se detecta un error.  
  
```javascript  
try  
    {  
        var x = y.name;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo establecer y luego obtener la pila.  
  
```javascript  
try  
    {  
        var err = Error("my error");  
        err.stack = "my stack trace";  
        throw err;  
    }  
catch(e)  
    {  
        document.write ("Error stack: ")  
        document.write (e.stack);  
    }  
```  
  
## Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]  
  
 **Se aplica a**: [Error \(Objeto\)](../../javascript/reference/error-object-javascript.md)  
  
## Vea también  
 [description \(Propiedad, Error\)](../../javascript/reference/description-property-error-javascript.md)   
 [message \(Propiedad, Error\)](../../javascript/reference/message-property-error-javascript.md)   
 [name \(Propiedad, Error\)](../../javascript/reference/name-property-error-javascript.md)   
 [stackTraceLimit \(Propiedad, Error\)](../../javascript/reference/stacktracelimit-property-error-javascript.md)