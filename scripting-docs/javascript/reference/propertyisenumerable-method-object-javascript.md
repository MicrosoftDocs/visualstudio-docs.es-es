---
title: "propertyIsEnumerable (M&#233;todo, Object de JavaScript) | Microsoft Docs"
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
  - "propertyIsEnumerable"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "propertyIsEnumerable (propiedad)"
ms.assetid: d90c7c2e-ea23-4710-a957-9aefbbd1f68b
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# propertyIsEnumerable (M&#233;todo, Object de JavaScript)
Determina si una propiedad especificada es enumerable.  
  
## Sintaxis  
  
```  
  
object. propertyIsEnumerable(proName)  
```  
  
## Parámetros  
 `object`  
 Obligatorio.  Instancia de un objeto.  
  
 `proName`  
 Obligatorio.  Valor alfanumérico de un nombre de propiedad.  
  
## Comentarios  
 El método `propertyIsEnumerable` devuelve `true` si `proName` existe en `object` y se puede enumerar mediante un bucle `For`.  El método `propertyIsEnumerable` devuelve `false` si `object` no tiene una propiedad con el nombre especificado o si la propiedad especificada no se puede enumerar.  Normalmente, las propiedades predefinidas no son enumerables, mientras que las propiedades definidas por el usuario siempre lo son.  
  
 El método `propertyIsEnumerable` no tiene en cuenta los objetos de la cadena de prototipo.  
  
## Ejemplo  
  
```javascript  
var a = new Array("apple", "banana", "cactus");  
document.write(a.propertyIsEnumerable(1));  
  
// Output: true  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vea también  
 [prototype \(Propiedad, Object\)](../../javascript/reference/prototype-property-object-javascript.md)