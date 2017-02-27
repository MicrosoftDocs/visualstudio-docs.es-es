---
title: "CA1505: Evitar el c&#243;digo dif&#237;cil de mantener | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidUnmaintainableCode"
  - "CA1505"
helpviewer_keywords: 
  - "AvoidUnmaintainableCode"
  - "CA1505"
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA1505: Evitar el c&#243;digo dif&#237;cil de mantener
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidUnmantainableCode|  
|Identificador de comprobación|CA1505|  
|Categoría|Microsoft.Maintainability|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un tipo o método tiene un valor del índice de mantenimiento bajo.  
  
## Descripción de la regla  
 El índice de mantenimiento se calcula utilizando las métricas siguientes: líneas de código, volumen del programa y complejidad ciclomática.  El volumen del programa es una medida de la dificultad de comprensión de un tipo o método que se basa en el número de operadores y operandos del código.  La complejidad ciclomática es una medida de la complejidad estructural del tipo o método.  Se puede obtener más información sobre métricas de código en [Medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).  
  
 Un índice de mantenimiento bajo indica que un tipo o método resulta probablemente difícil de mantener y se debería volver a diseñar.  
  
## Cómo corregir infracciones  
 Para corregir esta infracción, vuelva a diseñar el tipo o método e intente dividirlo en tipos o métodos más pequeños y concretos.  
  
## Cuándo suprimir advertencias  
 Excluya esta advertencia cuando un tipo o método todavía se considera fácil de mantener a pesar de su gran tamaño o cuando el tipo o método no se puede dividir.  
  
## Vea también  
 [Advertencias de mantenimiento](../code-quality/maintainability-warnings.md)   
 [Medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)