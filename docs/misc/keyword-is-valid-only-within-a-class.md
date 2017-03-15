---
title: "&#39;&lt;palabraClave&gt;&#39; solo es v&#225;lida dentro de una clase. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32002"
  - "vbc32002"
helpviewer_keywords: 
  - "BC32002"
ms.assetid: 773d8d50-abb8-4257-83a5-6e017c199d82
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;palabraClave&gt;&#39; solo es v&#225;lida dentro de una clase.
Una palabra clave relativa a clases, como `Me` o `MyClass`, se usa fuera de una definición de clase.  
  
 **Identificador de error:** BC32002  
  
### Para corregir este error  
  
-   Si el código que usa la palabra clave involucra instancias de clases, muévalo a una implementación de la clase.  
  
-   Si el código que usa la palabra clave no se aplica a clases, elimine la palabra clave no válida.  
  
## Vea también  
 [Me](http://msdn.microsoft.com/es-es/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [MyClass: eliminar](http://msdn.microsoft.com/es-es/5db36f9b-f796-4b6a-ba34-cac1fde6eb62)   
 [Class \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/class-statement)