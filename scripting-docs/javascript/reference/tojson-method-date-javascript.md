---
title: "toJSON (M&#233;todo, Date de JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toJSON (método)"
ms.assetid: f91df030-e9c9-425e-8e6d-b46bdda66cb6
caps.latest.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 27
---
# toJSON (M&#233;todo, Date de JavaScript)
Lo usa el método [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md) para habilitar la transformación de los datos de un objeto para la serialización de notación de objetos JavaScript \(JSON\).  
  
## Sintaxis  
  
```  
  
objectname.toJSON()  
```  
  
## Parámetros  
 `objectname`  
 Obligatorio.  Objeto para el que deseas la serialización de JSON.  
  
## Comentarios  
 La función `JSON.stringify` usa el método `toJSON`.  `JSON.stringify` serializa un valor de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] en texto JSON.  Si se proporciona un método `toJSON` a `JSON.stringify`, se llama al método `toJSON` cuando se llama a `JSON.stringify`.  
  
 El método `toJSON` es un miembro integrado del objeto [Date](../../javascript/reference/date-object-javascript.md) de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Devuelve una cadena de fecha con formato ISO para la zona horaria UTC \(se indica mediante el sufijo Z\).  
  
 Puedes invalidar el método `toJSON` para el tipo `Date` o definir un método `toJSON` para otros tipos de objeto con el fin de conseguir la transformación de datos para el tipo de objeto específico antes de la serialización de JSON.  
  
## Ejemplo  
 En el ejemplo siguiente se usa el método `toJSON` para serializar valores miembro de cadena en mayúsculas.  Se llama al método `toJSON` cuando se llama a `JSON.stringify`.  
  
```javascript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
contact.toJSON = function(key)  
 {  
    var replacement = new Object();  
    for (var val in this)  
    {  
        if (typeof (this[val]) === 'string')  
            replacement[val] = this[val].toUpperCase();  
        else  
            replacement[val] = this[val]  
    }  
    return replacement;  
};  
  
var jsonText = JSON.stringify(contact);  
  
/* The value of jsonText is:  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo usar el método `toJSON` que es un miembro integrado del objeto [Date](../../javascript/reference/date-object-javascript.md).  
  
```javascript  
var dt = new Date('8/24/2009');  
dt.setUTCHours(7, 30, 0);  
var jsonText = JSON.stringify(dt);  
  
/* The value of jsonText is:  
'"2009-08-24T07:30:00Z"'  
*/  
```  
  
## Requisitos  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)] **Se aplica a:** [Date \(Objeto\)](../../javascript/reference/date-object-javascript.md)  
  
## Vea también  
 [JSON \(Objeto\)](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse \(Función\)](../../javascript/reference/json-parse-function-javascript.md)   
 [JSON.stringify \(Función\)](../../javascript/reference/json-stringify-function-javascript.md)   
 [Métodos de JavaScript](../../javascript/reference/javascript-methods.md)