---
title: "get (M&#233;todo, Map de JavaScript) | Microsoft Docs"
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
ms.assetid: bebbd6bc-6e61-4674-8196-7e907798973f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# get (M&#233;todo, Map de JavaScript)
Devuelve un elemento especificado de un mapa.  
  
## Sintaxis  
  
```javascript  
mapObj.get(key)  
```  
  
#### Parámetros  
 `mapObj`  
 Requerido.  Un objeto `Map`.  
  
 `key`  
 Requerido.  La clave de un elemento en `Map`.  
  
## Valor de propiedad y valor devuelto  
 Devuelve el objeto asociado con la clave.  Si `Map` no contiene la clave, este método devuelve un valor de `undefined`.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo recuperar un elemento desde un objeto `Map`.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
document.write(m.get(2));  
  
// Output:  
// red  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]