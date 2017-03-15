---
title: "El argumento de tipo &#39;&lt;nombreArgumentoTipo&gt;&#39; debe tener un constructor de instancia sin par&#225;metros p&#250;blico para satisfacer la restricci&#243;n &#39;New&#39; para el par&#225;metro de tipo &#39;&lt;nombrePar&#225;metroTipo&gt;&#39;. | Microsoft Docs"
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
  - "vbc32083"
  - "BC32083"
helpviewer_keywords: 
  - "BC32083"
ms.assetid: 56bf25f1-375c-4b5d-9969-45eba8b3b66c
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El argumento de tipo &#39;&lt;nombreArgumentoTipo&gt;&#39; debe tener un constructor de instancia sin par&#225;metros p&#250;blico para satisfacer la restricci&#243;n &#39;New&#39; para el par&#225;metro de tipo &#39;&lt;nombrePar&#225;metroTipo&gt;&#39;.
Un argumento de tipo proporciona un tipo sin un constructor sin parámetros accesible a un parámetro de tipo con la restricción [New \(Operador\)](/dotnet/visual-basic/language-reference/operators/new-operator).  
  
 Una lista de restricciones impone requisitos al argumento de tipo pasado al parámetro de tipo. Un posible requisito es que el argumento de tipo deba exponer un constructor sin parámetros al que el código de creación pueda tener acceso. Para especificar este requisito, la lista de restricciones incluye la restricción `New`.  
  
 **Identificador de error:** BC32083  
  
### Para corregir este error  
  
1.  Compruebe que el nombre de tipo genérico y el nombre del tipo del argumento de tipo se han escrito correctamente.  
  
2.  Elija un tipo para el argumento de tipo que expone un constructor sin parámetros accesible. No se puede invocar este tipo genérico concreto a menos que se pueda proporcionar un argumento de tipo para este parámetro de tipo.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Cómo: Utilizar una clase genérica](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)