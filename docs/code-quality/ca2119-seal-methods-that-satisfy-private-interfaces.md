---
title: "CA2119: Sellar los m&#233;todos que cumplan las interfaces privadas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SealMethodsThatSatisfyPrivateInterfaces"
  - "CA2119"
helpviewer_keywords: 
  - "CA2119"
  - "SealMethodsThatSatisfyPrivateInterfaces"
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA2119: Sellar los m&#233;todos que cumplan las interfaces privadas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|  
|Identificador de comprobación|CA2119|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo público heredable proporciona una implementación de método reemplazable de una interfaz `internal` \(`Friend` en Visual Basic\).  
  
## Descripción de la regla  
 Los métodos de interfaz tienen accesibilidad pública y el tipo de implementación no lo puede cambiar.  Una interfaz interna crea un contrato que no está destinado a implementarse fuera del ensamblado que define la interfaz.  Un tipo público que implementa un método de una interfaz interna utilizando el modificador `virtual` \(`Overridable` en Visual Basic\) permite reemplazar el método por un tipo derivado que se encuentra fuera del ensamblado.  Si un segundo tipo del ensamblado de definición llama al método y espera un contrato exclusivamente interno, esto podría afectar al rendimiento si, en su lugar, se ejecuta el método reemplazado en el ensamblado externo.  Esto crea una vulnerabilidad de seguridad.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, evite que el método se invalide fuera del ensamblado; para ello, utilice una de las opciones siguientes:  
  
-   Haga que el tipo declarativo sea `sealed` \(`NotInheritable` en Visual Basic\).  
  
-   Cambie la accesibilidad del tipo declarativo a `internal` \(`Friend` en Visual Basic\).  
  
-   Quite todos los constructores públicos del tipo declarativo.  
  
-   Implemente el método sin utilizar el modificador `virtual`.  
  
-   Implemente el método de manera explícita.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si, después de una revisión atenta, se comprueba que no existe ningún problema de seguridad que pueda aprovecharse en caso de que el método se invalide fuera del ensamblado.  
  
## Ejemplo  
 El siguiente ejemplo muestra un tipo \(`BaseImplementation`\) que infringe esta regla.  
  
 [!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
 [!code-cs[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
 [!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]  
  
## Ejemplo  
 El ejemplo siguiente se aprovecha de la implementación del método virtual del ejemplo anterior.  
  
 [!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
 [!code-cs[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
 [!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]  
  
## Vea también  
 [Interfaces](/dotnet/csharp/programming-guide/interfaces/index)   
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)