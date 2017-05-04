---
title: "prototype (Propiedad, Intl.NumberFormat) | Microsoft Docs"
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
ms.assetid: 7f6a7e26-108b-4b32-97c2-7f96b9252c50
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# prototype (Propiedad, Intl.NumberFormat)
Devuelve una referencia al prototipo para un formateador.  
  
## Sintaxis  
  
```javascript  
numberFormat.prototype  
```  
  
## Comentarios  
 El argumento `numberFormat` es el nombre de un formateador.  
  
 Utilice la propiedad `prototype` para proporcionar un conjunto base de funcionalidad a una clase de objetos.  Las nuevas instancias de un objeto "heredan" el comportamiento del prototipo asignado a ese objeto.  
  
 Por ejemplo, para agregar un método al objeto `Intl.NumberFormat` que devuelve el valor del elemento mayor del conjunto, declare la función, agréguela a `Intl.NumberFormat.prototype` y después úsela.  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]