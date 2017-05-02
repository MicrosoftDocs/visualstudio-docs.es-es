---
title: "constructor (Propiedad, Boolean) | Microsoft Docs"
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
ms.assetid: b67ca875-23c6-4687-a5ce-1cdd25d1c923
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# constructor (Propiedad, Boolean)
Especifica la función que crea un objeto Boolean.  
  
## Sintaxis  
  
```  
  
boolean.constructor([[value])  
```  
  
#### Parámetros  
 `boolean`  
 Nombre del objeto Boolean.  
  
 `value`  
 Opcional.  Especifica el valor del objeto Boolean.  Puede ser los números 1 o 0, o las cadenas "true" o "false".  
  
## Comentarios  
 La propiedad `constructor` contiene una referencia a la función que crea instancias del objeto Boolean.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso de la propiedad constructor.  
  
```javascript  
var x = new Boolean("true");  
  
if (x.constructor == Boolean)  
    document.write("Object is a Boolelan.");  
  
// Output:  
// Object is a Boolean.  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]