---
title: "La estructura &#39;&lt;nombreDeEstructura&gt;&#39; no puede contener una instancia de s&#237; misma: &lt;error&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30294"
  - "bc30294"
helpviewer_keywords: 
  - "BC30294"
ms.assetid: 17780e11-2425-4860-9345-b5db019d2bf3
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La estructura &#39;&lt;nombreDeEstructura&gt;&#39; no puede contener una instancia de s&#237; misma: &lt;error&gt;
Una estructura declara una variable y la inicializa con una instancia de sí misma.  
  
 Una estructura puede contener instancias de otras estructuras, pero no una instancia interna de sí misma. Un intento de hacerlo provocaría una recursividad infinita.  
  
 **Identificador de error:** BC30294  
  
### Para corregir este error  
  
1.  Compruebe la ortografía de la expresión de inicialización en la instrucción de declaración.  
  
2.  Si tiene previsto crear otra instancia de la misma estructura, debe declararla y crearla fuera de la estructura.  
  
## Vea también  
 [Estructuras](/dotnet/visual-basic/programming-guide/language-features/data-types/structures)   
 [Structure \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/structure-statement)