---
title: "JSON (Objeto de JavaScript) | Microsoft Docs"
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
  - "JSON"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JSON (objeto)"
ms.assetid: 0279a0e0-70bf-451a-a78e-0da4e2fdeb9a
caps.latest.revision: 43
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 43
---
# JSON (Objeto de JavaScript)
Objeto intrínseco que proporciona dos funciones para convertir valores de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] a y desde el formato de notación de objetos JavaScript \(JSON\).  La función `JSON.stringify` serializa un valor de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] en texto JSON.  La función `JSON.parse` deserializa el texto JSON para generar un valor de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Sintaxis  
  
```  
  
JSON.[method]  
  
```  
  
## Parámetros  
 `Method`  
 Requerido.  Nombre de uno de los métodos del objeto `JSON`.  
  
## Comentarios  
 No se puede crear un objeto `JSON` con el operador `new`.  Si intenta hacerlo, se genera un error.  Sin embargo, puede invalidar o modificar el objeto `JSON`.  
  
 El motor de scripting crea el objeto `JSON` cuando se carga.  Sus métodos están a disposición del script en todo momento.  
  
 Para usar el objeto `JSON` intrínseco, asegúrese de no invalidarlo con otro objeto `JSON` definido en el script.  Puede que tenga que modificar instrucciones existentes del script que detectan la presencia de un objeto `JSON`, porque estas instrucciones se evalúan de manera diferente.  Esto último se muestra en el ejemplo siguiente.  
  
```javascript  
if (!this.JSON) {  
    // JSON object does not exist.  
    }  
```  
  
 En el ejemplo anterior, `!this.JSON` se evalúa como false en [!INCLUDE[jsv58text](../../javascript/reference/includes/jsv58text-md.md)].  Por lo tanto, el código que hay dentro de la instrucción `if` no se ejecuta.  
  
## Funciones  
 [JSON.parse \(Función\)](../../javascript/reference/json-parse-function-javascript.md)  
  
 [JSON.stringify \(Función\)](../../javascript/reference/json-stringify-function-javascript.md)  
  
## Requisitos  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## Vea también  
 [toJSON \(Método, Date\)](../../javascript/reference/tojson-method-date-javascript.md)   
 [Objetos de JavaScript](../../javascript/reference/javascript-objects.md)   
 [Aplicación de ejemplo de la plantilla Hub \(Tienda Windows\)](http://code.msdn.microsoft.com/Hub-template-sample-with-4b70002d)