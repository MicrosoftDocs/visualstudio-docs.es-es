---
title: "No se puede asignar a &#39;this&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5000"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# No se puede asignar a &#39;this&#39;
Has intentado asignar un valor a **this**.  **this** es una palabra clave de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que hace referencia a uno de los siguientes elementos:  
  
-   el objeto que está ejecutando actualmente un método,  
  
-   el objeto global si no hay ningún método actual \(o si el método no pertenece a ningún otro objeto\).  
  
 Un método es una función de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] que se invoca a través de un objeto.  En un método, la palabra clave **this** es una referencia al objeto a través del cual se invocó el método \(que es el objeto creado al invocar el constructor de clase con el operador **new**\).  
  
 En un método, puedes usar **this** para hacer referencia al objeto actual, pero no puedes asignar un valor nuevo a **this**.  
  
### Para corregir este error  
  
-   No intentes asignar ningún valor a **this**.  Para tener acceso a una propiedad o un método de una instancia de un objeto, usa el operador punto \(por ejemplo, círculo**.**radio\).  
  
    > [!NOTE]
    >  No puedes asignar el nombre **this** a una variable creada por el usuario; se trata de una palabra reservada de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Vea también  
 [this \(Instrucción\)](../../javascript/reference/this-statement-javascript.md)   
 [Solución de problemas en las secuencias de comandos](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)