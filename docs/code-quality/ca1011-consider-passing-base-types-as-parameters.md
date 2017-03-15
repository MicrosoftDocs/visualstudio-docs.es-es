---
title: "CA1011: Considere pasar los tipos base como par&#225;metros | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ConsiderPassingBaseTypesAsParameters"
  - "CA1011"
helpviewer_keywords: 
  - "CA1011"
  - "ConsiderPassingBaseTypesAsParameters"
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1011: Considere pasar los tipos base como par&#225;metros
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ConsiderPassingBaseTypesAsParameters|  
|Identificador de comprobación|CA1011|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Una declaración de método incluye un parámetro formal que es un tipo derivado y el método solo llama a los miembros del tipo base del parámetro.  
  
## Descripción de la regla  
 Cuando en una declaración de método se especifica un tipo base como parámetro, cualquier tipo derivado del tipo base puede pasarse al método como el argumento correspondiente.  Cuando el argumento se utiliza dentro del cuerpo del método, el método específico que se ejecuta depende del tipo del argumento.  Si la funcionalidad adicional proporcionada por el tipo derivado no resulta necesaria, el uso del tipo base permite que el método se utilice más ampliamente.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el tipo del parámetro a su tipo base.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla  
  
-   si el método requiere la funcionalidad concreta proporcionada por el tipo derivado  
  
     – O bien –  
  
-   para exigir que solo se pase al método el tipo derivado o un tipo más derivado.  
  
 En estos casos, el código será más sólido debido a la comprobación de tipos fuertes proporcionada por el compilador y el motor en tiempo de ejecución.  
  
## Ejemplo  
 El ejemplo siguiente muestra un método, `ManipulateFileStream`, que solo se puede utilizar con un objeto <xref:System.IO.FileStream>, que infringe esta regla.  Un segundo método, `ManipulateAnyStream`, cumple la regla reemplazando el parámetro <xref:System.IO.FileStream> mediante <xref:System.IO.Stream>.  
  
 [!code-cs[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]  
  
## Reglas relacionadas  
 [CA1059: Los miembros no deben exponer determinados tipos concretos](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)