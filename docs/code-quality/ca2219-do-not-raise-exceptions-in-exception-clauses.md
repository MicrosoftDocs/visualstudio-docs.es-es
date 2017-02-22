---
title: "CA2219: No producir excepciones en cl&#225;usulas de excepci&#243;n | Microsoft Docs"
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
  - "DoNotRaiseExceptionsInExceptionClauses"
  - "CA2219"
helpviewer_keywords: 
  - "CA2219"
  - "DoNotRaiseExceptionsInExceptionClauses"
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2219: No producir excepciones en cl&#225;usulas de excepci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotRaiseExceptionsInExceptionClauses|  
|Identificador de comprobación|CA2219|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No problemático, Problemático|  
  
## Motivo  
 Se inicia una excepción desde una cláusula `finally`, de filtro o de error.  
  
## Descripción de la regla  
 Cuando se inicia una excepción en una cláusula de excepción, aumenta notablemente la dificultad de depuración.  
  
 Cuando se inicia una excepción en una cláusula `finally` o de error, la nueva excepción oculta la excepción activa, si existe.  Esto hace que el error original sea difícil de detectar y depurar.  
  
 Cuando se inicia una excepción en una cláusula de filtro, el motor en tiempo de ejecución la detecta automáticamente y hace que el filtro se evalúe como false.  No hay ninguna manera de indicar la diferencia entre el filtro que se evalúa como false y una excepción que se inicia desde un filtro.  Esto dificulta la detección y depuración de errores en la lógica del filtro.  
  
## Cómo corregir infracciones  
 Para corregir esta infracción de la regla, no produzca explícitamente una excepción en una cláusula `finally`, de filtro o de error.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  No hay ningún escenario en el que una excepción iniciada en una cláusula de excepción proporcione ventajas al código que se ejecuta.  
  
## Reglas relacionadas  
 [CA1065: No producir excepciones en ubicaciones inesperadas](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)  
  
## Vea también  
 [Diseñar advertencias](../code-quality/design-warnings.md)