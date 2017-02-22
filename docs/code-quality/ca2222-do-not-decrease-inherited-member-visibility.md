---
title: "CA2222: No reducir la visibilidad del miembro heredado | Microsoft Docs"
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
  - "DoNotDecreaseInheritedMemberVisibility"
  - "CA2222"
helpviewer_keywords: 
  - "CA2222"
  - "DoNotDecreaseInheritedMemberVisibility"
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2222: No reducir la visibilidad del miembro heredado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDecreaseInheritedMemberVisibility|  
|Identificador de comprobación|CA2222|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Un método privado en un tipo no sellado tiene una firma que es idéntica a un método público declarado en un tipo base.  El método privado no es final.  
  
## Descripción de la regla  
 No debería cambiar el modificador de acceso para los miembros heredados.  Cambiando un miembro heredado a privado no evita que los llamadores tengan acceso a la implementación de la clase base del método.  Si el miembro se cambia a privado y el tipo es no sellado, los tipos heredados pueden llamar a la última implementación pública del método de la jerarquía de herencia.  Si debe cambiar el modificador de acceso, debe marcase el método como final o debe sellarse el tipo para evitar que el método se reemplace.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el acceso para ser no privado.  Alternativamente, si su lenguaje de programación lo admite, puede hacer que el método sea final.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El siguiente ejemplo muestra un tipo que infringe esta regla.  
  
 [!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
 [!code-cs[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]