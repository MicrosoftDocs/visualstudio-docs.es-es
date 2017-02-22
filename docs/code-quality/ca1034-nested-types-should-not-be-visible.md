---
title: "CA1034: Los tipos anidados no deben ser visibles | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "NestedTypesShouldNotBeVisible"
  - "CA1034"
helpviewer_keywords: 
  - "NestedTypesShouldNotBeVisible"
  - "CA1034"
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1034: Los tipos anidados no deben ser visibles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|NestedTypesShouldNotBeVisible|  
|Identificador de comprobación|CA1034|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo visible externamente contiene una declaración de tipos visible externamente.  Las enumeraciones anidadas y los tipos protegidos están exentos de esta regla.  
  
## Descripción de la regla  
 Los tipos anidados son tipos declarados dentro del ámbito de otro tipo.  Los tipos anidados son útiles para encapsular los detalles de la implementación privada del tipo contenido.  Los tipos anidados, utilizados para este propósito, no deben ser visibles externamente.  
  
 No utilice tipos anidados visibles externamente para agrupar de forma lógica o evitar las colisiones del nombre; en su lugar, utilice los espacios de nombres.  
  
 Los tipos anidados incluyen la noción de accesibilidad de miembro, que algunos programadores no entienden claramente.  
  
 Los tipos protegidos se pueden utilizar en subclases y los tipos anidados en escenarios de personalización avanzada.  
  
## Cómo corregir infracciones  
 Si no desea que el tipo anidado esté visible externamente, cambie la accesibilidad del tipo.  De lo contrario, quite el tipo anidado de su elemento primario.  Si el propósito del anidamiento es clasificar el tipo anidado, utilice un espacio de nombres para crear la jerarquía en su lugar.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El siguiente ejemplo muestra un tipo que infringe la regla.  
  
 [!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
 [!code-cs[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]