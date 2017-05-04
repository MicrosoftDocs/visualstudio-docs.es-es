---
title: "hasOwnProperty (M&#233;todo, Object de JavaScript) | Microsoft Docs"
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
  - "hasOwnProperty"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "hasOwnProperty (método)"
ms.assetid: 3eb69d69-486f-4792-9518-4452aef369ca
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# hasOwnProperty (M&#233;todo, Object de JavaScript)
Determina si un objeto tiene una propiedad con el nombre especificado.  
  
## Sintaxis  
  
```  
  
object.hasOwnProperty(proName)  
```  
  
## Parámetros  
 `object`  
 Requerido.  Instancia de un objeto.  
  
 `proName`  
 Requerido.  Valor de cadena de un nombre de propiedad.  
  
## Comentarios  
 El método `hasOwnProperty` devuelve `true` si `object` tiene una propiedad con el nombre especificado y `false` si no la tiene.  Este método no comprueba las propiedades de la cadena de prototipo del objeto; la propiedad debe ser miembro del propio objeto.  
  
 Esta propiedad no se admite en los objetos host de Internet Explorer 8 y versiones anteriores.  
  
## Ejemplo  
 En el ejemplo siguiente, todos los objetos `String` comparten un método split común.  El código siguiente mostrará **false** y **true**.  
  
```javascript  
var s = new String("Sample");  
document.write(s.hasOwnProperty("split"));  
document.write("<br/>");  
document.write(String.prototype.hasOwnProperty("split"));  
  
// Output:  
// false  
// true  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vea también  
 [in \(Operador\)](../../javascript/reference/in-operator-decrementjavascript.md)