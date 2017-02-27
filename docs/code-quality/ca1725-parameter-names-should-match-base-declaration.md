---
title: "CA1725: Los nombres de par&#225;metro deber&#237;an coincidir con la declaraci&#243;n base | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ParameterNamesShouldMatchBaseDeclaration"
  - "CA1725"
helpviewer_keywords: 
  - "CA1725"
  - "ParameterNamesShouldMatchBaseDeclaration"
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA1725: Los nombres de par&#225;metro deber&#237;an coincidir con la declaraci&#243;n base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ParameterNamesShouldMatchBaseDeclaration|  
|Identificador de comprobación|CA1725|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático|  
  
## Motivo  
 El nombre de un parámetro en un reemplazo de método visible externamente no coincide con el nombre del parámetro de la declaración base del método o con el nombre del parámetro en la declaración de interfaz del método.  
  
## Descripción de la regla  
 El uso del mismo nombre para un parámetro en una jerarquía de reemplazo aumenta la utilidad de los reemplazos de método.  Cuando el nombre de un parámetro en un método derivado es distinto del nombre de la declaración base, puede resultar difícil determinar si el método es un reemplazo del método base o una nueva sobrecarga del método.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el nombre del parámetro de modo que sea el mismo que en la declaración base.  La corrección es un cambio problemático para los métodos visibles para COM.  
  
## Cuándo suprimir advertencias  
 No suprima ninguna advertencia de esta regla excepto para los métodos que se vean de COM en bibliotecas que se hayan distribuido previamente.