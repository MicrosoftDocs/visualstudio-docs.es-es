---
title: "CA1048: No declarar miembros virtuales en tipos sealed | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotDeclareVirtualMembersInSealedTypes"
  - "CA1048"
helpviewer_keywords: 
  - "CA1048"
  - "DoNotDeclareVirtualMembersInSealedTypes"
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA1048: No declarar miembros virtuales en tipos sealed
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|  
|Identificador de comprobación|CA1048|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo público es sealed y declara un método que tanto `virtual` \(`Overridable` en Visual Basic\) como no final.  Esta regla no crea un informe sobre las infracciones para los tipos de delegado, que deben seguir este modelo.  
  
## Descripción de la regla  
 Los tipos declaran los métodos como virtuales para que los tipos heredados puedan reemplazar la implementación del método virtual.  Por definición, no se puede heredar de un tipo sealed, haciendo que un método virtual de un de tipo sealed no tenga sentido.  
  
 Los compiladores de Visual Basic .NET y de C\# no permiten que los tipos infrinjan esta regla.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, marque el método como no virtual o haga que el tipo sea heredable.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  Si se mantiene el estado actual del tipo puede provocar problemas de mantenimiento y no proporciona ventajas.  
  
## Ejemplo  
 El siguiente ejemplo muestra un tipo que infringe esta regla.  
  
 [!code-cpp[FxCop.Design.SealedVirtual#1](../code-quality/codesnippet/CPP/ca1048-do-not-declare-virtual-members-in-sealed-types_1.cpp)]