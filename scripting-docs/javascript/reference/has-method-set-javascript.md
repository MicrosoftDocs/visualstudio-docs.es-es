---
title: "has (M&#233;todo, Set de JavaScript) | Microsoft Docs"
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
ms.assetid: fb80f2e0-fc5e-4508-af14-1c3b3b833636
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# has (M&#233;todo, Set de JavaScript)
Devuelve el objeto `true` si el conjunto contiene el elemento especificado.  
  
## Sintaxis  
  
```javascript  
setObj.has(value)  
```  
  
#### Parámetros  
 `setObj`  
 Requerido.  Un objeto `Set`.  
  
 `value`  
 Requerido.  Elemento que se va a comprobar.  
  
## Valor de propiedad y valor devuelto  
 `true` si el conjunto contiene el elemento especificado.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo agregar miembros a `Set` y después comprobar si el conjunto contiene un miembro específico.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
  
document.write(s.has(1776));  
document.write(s.has("1776"));  
  
// Output:  
// true  
// false  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]