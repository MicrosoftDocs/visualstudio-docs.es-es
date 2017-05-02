---
title: "isPrototypeOf (M&#233;todo, Object de JavaScript) | Microsoft Docs"
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
  - "isPrototypeOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "isPrototypeOf (método)"
ms.assetid: 9c821319-c208-480f-915e-565ef6e017b6
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# isPrototypeOf (M&#233;todo, Object de JavaScript)
Determina si un objeto existe en la cadena de prototipo de otro objeto.  
  
## Sintaxis  
  
```  
  
prototype.isPrototypeOf(object)  
```  
  
## Parámetros  
 `prototype`  
 Obligatorio.  Prototipo del objeto.  
  
 `object`  
 Obligatorio.  Otro objeto cuya cadena de prototipo se va a comprobar.  
  
## Comentarios  
 El método `isPrototypeOf` devuelve `true` si `object` tiene `prototype` en su cadena de prototipo.  La cadena de prototipo se utiliza para compartir la funcionalidad entre instancias del mismo tipo de objetos.  El método `isPrototypeOf` devuelve `false` cuando `object` no es un objeto o cuando `prototype` no aparece en la cadena de prototipo de `object`.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `isPrototypeOf`.  
  
```javascript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
document.write(Rectangle.prototype.isPrototypeOf(rec));  
  
// Output: true  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vea también  
 [prototype \(Propiedad, Object\)](../../javascript/reference/prototype-property-object-javascript.md)