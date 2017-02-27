---
title: "CA1047: No declarar miembros protegidos en tipos sealed | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotDeclareProtectedMembersInSealedTypes"
  - "CA1047"
helpviewer_keywords: 
  - "CA1047"
  - "DoNotDeclareProtectedMembersInSealedTypes"
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1047: No declarar miembros protegidos en tipos sealed
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|  
|Identificador de comprobación|CA1047|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un tipo público es `sealed` \(`NotInheritable` en Visual Basic\) y declara un miembro protegido o un tipo anidado protegido.  Esta regla no realiza ningún informe sobre las infracciones para los métodos <xref:System.Object.Finalize%2A>, que deben seguir este modelo.  
  
## Descripción de la regla  
 Los tipos declaran miembros protegidos para que los tipos heredados puedan obtener acceso o reemplazar el miembro.  Por definición, no se puede heredar de un tipo sealed, lo que significa que no se puede llamar a los métodos protegidos en tipos sealed.  
  
 El compilador de C\# emite una advertencia para este error.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el nivel de acceso del miembro a privado o cambie el tipo a heredable.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  Si se mantiene el estado actual del tipo puede provocar problemas de mantenimiento y no proporciona ventajas.  
  
## Ejemplo  
 El siguiente ejemplo muestra un tipo que infringe esta regla.  
  
 [!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
 [!code-cs[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]