---
title: "prototype (Propiedad, Intl.Collator) | Microsoft Docs"
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
ms.assetid: c1bbb523-fb55-4395-b357-34d91cf5bba0
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# prototype (Propiedad, Intl.Collator)
Devuelve una referencia al prototipo para un intercalador.  
  
## Sintaxis  
  
```javascript  
collator.prototype  
```  
  
## Comentarios  
 El argumento `collator` es el nombre de un intercalador.  
  
 Utilice la propiedad `prototype` para proporcionar un conjunto base de funcionalidad a una clase de objetos.  Las nuevas instancias de un objeto "heredan" el comportamiento del prototipo asignado a ese objeto.  
  
 Por ejemplo, para agregar un método al objeto `Intl.Collator` que devuelve el valor del elemento mayor del conjunto, declare la función, agréguela a `Intl.Collator.prototype` y después úsela.  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]