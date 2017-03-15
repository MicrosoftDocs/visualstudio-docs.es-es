---
title: "CA2121: Los constructores est&#225;ticos deber&#237;an ser privados | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2121"
  - "StaticConstructorsShouldBePrivate"
helpviewer_keywords: 
  - "CA2121"
  - "StaticConstructorsShouldBePrivate"
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2121: Los constructores est&#225;ticos deber&#237;an ser privados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|StaticConstructorsShouldBePrivate|  
|Identificador de comprobación|CA2121|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo tiene un constructor estático que no es privado.  
  
## Descripción de la regla  
 Los constructores estáticos, también denominado constructores de clase, se utilizan para inicializar un tipo.  El sistema llama al constructor estático antes de crear la primera instancia del tipo o antes de hacer referencia a cualquier miembro estático.  El usuario no tiene ningún control sobre cuándo se llama al constructor estático.  Si un constructor estático no es privado, se puede llamar a través de un código distinto del sistema.  En función de las operaciones que se realizan en el constructor, esto puede producir un comportamiento inesperado.  
  
 Los compiladores de C\# y Visual Basic .NET exigen esta regla.  
  
## Cómo corregir infracciones  
 Una de las acciones siguientes normalmente provoca las infracciones:  
  
-   Se definió un constructor estático para su tipo y no lo estableció como privado.  
  
-   El compilador del lenguaje de programación agregó un constructor estático predeterminado a su tipo y no lo estableció como privado.  
  
 Para corregir el primer tipo de infracción, establezca su constructor estático como privado.  Para corregir el segundo tipo, agregue un constructor estático privado a su tipo.  
  
## Cuándo suprimir advertencias  
 No suprima estas infracciones.  Si el diseño del software requiere una llamada explícita a un constructor estático, probablemente el diseño contenga errores graves y deberá revisarse.