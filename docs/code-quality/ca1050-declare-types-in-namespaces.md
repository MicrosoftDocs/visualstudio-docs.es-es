---
title: "CA1050: Declare tipos en espacios de nombres | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1050"
  - "DeclareTypesInNamespaces"
helpviewer_keywords: 
  - "CA1050"
  - "DeclareTypesInNamespaces"
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1050: Declare tipos en espacios de nombres
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DeclareTypesInNamespaces|  
|Identificador de comprobación|CA1050|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo público o protegido se define fuera del ámbito de un espacio de nombres.  
  
## Descripción de la regla  
 Los tipos se declaran en los espacios de nombres para evitar conflictos de nombre y como una forma de organizar los tipos relacionados en una jerarquía de objetos.  Los tipos que están fuera de cualquier espacio de nombres se encuentran en un espacio de nombres global al que no se puede hacer referencia en el código.  
  
## Cómo corregir infracciones  
 Para corregir las infracciones de esta regla, coloque el tipo en un espacio de nombres.  
  
## Cuándo suprimir advertencias  
 Aunque nunca tiene que suprimir una advertencia de esta regla, es seguro hacerlo cuando el ensamblado no se vaya a usar nunca junto con otros ensamblados.  
  
## Ejemplo  
 El siguiente ejemplo muestra una biblioteca con un tipo declarado incorrectamente fuera del espacio de nombres, y otro tipo con el mismo nombre declarado dentro del espacio de nombres.  
  
 [!code-cs[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]  
  
## Ejemplo  
 La aplicación siguiente utiliza la biblioteca definida previamente.  Tenga en cuenta que el tipo que se declara fuera de un espacio de nombres es creado cuando el nombre `Test` no está calificado por un espacio de nombres.  También observe que es necesario el nombre del espacio de nombres para obtener acceso al tipo `Test` en `Goodspace`.  
  
 [!code-cs[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_2.cs)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_2.vb)]