---
title: "CA1707: Los identificadores no deber&#237;an contener subrayado | Microsoft Docs"
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
  - "IdentifiersShouldNotContainUnderscores"
  - "CA1707"
helpviewer_keywords: 
  - "CA1707"
  - "IdentifiersShouldNotContainUnderscores"
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1707: Los identificadores no deber&#237;an contener subrayado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotContainUnderscores|  
|Identificador de comprobación|CA1707|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático: si se desencadena en ensamblados<br /><br /> No problemático: cuando se produce en parámetros de tipo|  
  
## Motivo  
 El nombre de un identificador contiene el carácter de subrayado \(\_\).  
  
## Descripción de la regla  
 Por convención, los nombres del identificador no contienen el carácter de subrayado \(\_\).  La regla comprueba espacios de nombres, tipos, miembros y parámetros.  
  
 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime.  Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.  
  
## Cómo corregir infracciones  
 Quite todos los caracteres de subrayado del nombre.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Reglas relacionadas  
 [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Los identificadores se deberían diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)