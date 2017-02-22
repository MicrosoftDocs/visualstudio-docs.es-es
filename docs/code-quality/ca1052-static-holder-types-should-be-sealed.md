---
title: "CA1052: Los tipos titulares est&#225;ticos deben ser sealed | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "StaticHolderTypesShouldBeSealed"
  - "CA1052"
helpviewer_keywords: 
  - "CA1052"
  - "StaticHolderTypesShouldBeSealed"
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1052: Los tipos titulares est&#225;ticos deben ser sealed
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|StaticHolderTypesShouldBeSealed|  
|Identificador de comprobación|CA1052|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo público o protegido sólo contiene miembros estáticos y no se declara con el modificador [sellado](/dotnet/csharp/language-reference/keywords/sealed) \([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)\).  
  
## Descripción de la regla  
 Esta regla supone que un tipo que sólo contiene miembros estáticos no está diseñado para heredarse, porque el tipo no proporciona ninguna funcionalidad que pueda reemplazarse con un tipo derivado.  Un tipo que no está diseñado para heredarse debería marcarse con el modificador `sealed` para prohibir su uso como tipo base.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, marque el tipo como `sealed`.  Si utiliza como destino [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] o una versión anterior, es mejor marcar el tipo como `static`.  De esta manera, evita tener que declarar un constructor privado para evitar que se cree la clase.  
  
## Cuándo suprimir advertencias  
 Suprima una advertencia de esta regla sólo si el tipo está diseñado para poder heredarse.  La ausencia del modificador `sealed` sugiere que el tipo sea útil como tipo base.  
  
## Ejemplo de infracción  
  
### Descripción  
 El siguiente ejemplo muestra un tipo que infringe la regla.  
  
### Código  
 [!code-cs[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]  
  
## Corregir con el modificador estático  
  
### Descripción  
 El ejemplo siguiente muestra cómo corregir una infracción de esta regla marcando el tipo con el modificador `static`.  
  
### Código  
 [!code-cs[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]  
  
## Reglas relacionadas  
 [CA1053: Los tipos titulares estáticos no deben tener constructores](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)