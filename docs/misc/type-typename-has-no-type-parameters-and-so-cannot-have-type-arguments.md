---
title: "El tipo &#39;&lt;nombreDeTipo&gt;&#39; no tiene par&#225;metros de tipo y, por lo tanto, no puede tener argumentos de tipo | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32045"
  - "vbc32045"
helpviewer_keywords: 
  - "BC32045"
ms.assetid: b86e784c-6718-4585-bd39-2f0982068828
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El tipo &#39;&lt;nombreDeTipo&gt;&#39; no tiene par&#225;metros de tipo y, por lo tanto, no puede tener argumentos de tipo
Una instrucción de declaración o de asignación incluye una cláusula [Of](/dotnet/visual-basic/language-reference/statements/of-clause) al invocar un tipo no genérico.  
  
 Por su definición, un *tipo genérico* es una clase, una estructura, una interfaz, un procedimiento o un delegado que actúa en tipos de datos y que se puede especificar a través de uno o varios *parámetros de tipo*. Si el código en uso crea un tipo de este tipo genérico, proporciona un *argumento de tipo* para cada parámetro de tipo. Como parte de la creación del tipo, cada argumento de tipo reemplaza cada aparición del parámetro de tipo correspondiente en el código generado.  
  
 Los parámetros de tipo se definen con una cláusula `Of` entre paréntesis y los argumentos de tipo se proporcionan con una cláusula `Of` entre paréntesis. La cláusula `Of` solo se usa cuando al trabajar con tipos genéricos.  
  
 Los tipos no genéricos no aceptan parámetros de tipo y no se puede especificar ningún argumento de tipo al invocar estos tipos.  
  
 **Identificador de error:** BC32045  
  
### Para corregir este error  
  
1.  Compruebe la ortografía del tipo que usa en la instrucción de declaración o de asignación.  
  
2.  Si invoca un tipo no genérico, quite la cláusula `Of` y sus paréntesis, si existen. No quite paréntesis que incluyan una lista de argumentos estándar para un procedimiento, delegado o constructor de clase.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Cómo: Utilizar una clase genérica](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)