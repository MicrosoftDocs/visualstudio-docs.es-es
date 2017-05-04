---
title: "has (M&#233;todo, Map de JavaScript) | Microsoft Docs"
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
ms.assetid: 876df854-2941-4db2-92c6-1b497840b169
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# has (M&#233;todo, Map de JavaScript)
Devuelve el objeto `true` si el mapa contiene el elemento especificado.  
  
## Sintaxis  
  
```javascript  
mapObj.has(key)  
```  
  
#### Parámetros  
 `mapObj`  
 Requerido.  Un objeto `Map`.  
  
 `key`  
 Requerido.  Clave del elemento que se va a probar.  
  
## Valor de propiedad y valor devuelto  
 `true` si la asignación contiene el elemento especificado.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo agregar un miembro a `Map` y después comprobar si la asignación lo contiene.  
  
```javascript  
var m = new Map();  
m.set(2, "red");  
  
document.write(m.has(2));  
  
// Output:  
// true  
```  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]