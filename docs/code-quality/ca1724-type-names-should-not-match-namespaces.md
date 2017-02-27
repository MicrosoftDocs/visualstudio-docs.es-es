---
title: "CA1724: Los nombres de tipo no deben coincidir con los espacios de nombres | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TypeNamesShouldNotMatchNamespaces"
  - "CA1724"
helpviewer_keywords: 
  - "TypeNamesShouldNotMatchNamespaces"
  - "CA1724"
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1724: Los nombres de tipo no deben coincidir con los espacios de nombres
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypeNamesShouldNotMatchNamespaces|  
|Identificador de comprobación|CA1724|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un nombre de tipo coincide con los nombres de un espacio de nombres de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] en una comparación sin distinción entre mayúsculas y minúsculas.  
  
## Descripción de la regla  
 Los nombres de tipo no deben coincidir con los nombres de espacios de nombres definidos en la biblioteca de clases de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Infringir esta regla puede reducir la utilidad de la biblioteca.  
  
## Cómo corregir infracciones  
 Seleccione un nombre de tipo que no coincide con el nombre de un espacio de nombres de la biblioteca de clases [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## Cuándo suprimir advertencias  
 Para el nuevo desarrollo, no se da ningún escenario conocido donde se deba suprimir ninguna advertencia de esta regla.  Antes de suprimir la advertencia, piense que el nombre que coincide podría confundir a los usuarios de la biblioteca.  Para enviar las bibliotecas, quizá deba suprimir una advertencia de esta regla.