---
title: "stackTraceLimit (Propiedad, Error de JavaScript) | Microsoft Docs"
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
  - "Error.stackTraceLimit"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "límite de seguimiento de pila de errores [JavaScript]"
  - "pila de errores de JavaScript"
  - "pila de errores [JavaScript]"
  - "límite de seguimiento de pila de JavaScript"
ms.assetid: 127ef8e8-892e-4263-9ebc-03364af01212
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# stackTraceLimit (Propiedad, Error de JavaScript)
Obtiene o establece el límite del seguimiento de pila, que equivale al número de marcos de error que se van a mostrar.  El límite predeterminado es 10.  
  
## Sintaxis  
  
```  
  
Error  
.stackTraceLimit   
```  
  
## Comentarios  
 Puede establecer la propiedad `stackTraceLimit` en cualquier valor positivo comprendido entre 0 e `Infinity`.  Si la propiedad `stackTraceLimit` se establece en 0 en el momento de producirse un error, no se muestra ningún seguimiento de la pila.  Si la propiedad se establece en un valor negativo o un valor no numérico, el valor se convierte en 0.  Si stackTraceLimit se establece en `Infinity`, se muestra la pila completa.  De lo contrario, `ToUint32` se utiliza para convertir el valor.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo establecer y, luego, obtener, el límite de seguimiento de pila.  
  
```javascript  
try  
    {  
    var err = new Error("my error");  
    Error.stackTraceLimit = 7;  
    throw err;  
    }  
catch(e)  
    {  
    document.write ("Error stack trace limit: ")  
    document.write (Error.stackTraceLimit);  
    }  
```  
  
## Requisitos  
 Se admite en aplicaciones de Internet Explorer 10 y [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
 **Se aplica a**: [Error \(Objeto\)](../../javascript/reference/error-object-javascript.md)  
  
## Vea también  
 [description \(Propiedad, Error\)](../../javascript/reference/description-property-error-javascript.md)   
 [message \(Propiedad, Error\)](../../javascript/reference/message-property-error-javascript.md)   
 [name \(Propiedad, Error\)](../../javascript/reference/name-property-error-javascript.md)   
 [stack \(Propiedad, Error\)](../../javascript/reference/stack-property-error-javascript.md)