---
title: "CA1061: No oculte m&#233;todos de clases base | Microsoft Docs"
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
  - "CA1061"
  - "DoNotHideBaseClassMethods"
helpviewer_keywords: 
  - "CA1061"
  - "DoNotHideBaseClassMethods"
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1061: No oculte m&#233;todos de clases base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotHideBaseClassMethods|  
|Identificador de comprobación|CA1061|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo derivado declara un método con el mismo nombre y el mismo número de parámetros que uno de sus métodos base; uno o varios de los parámetros es un tipo base del parámetro correspondiente en el método base; y los parámetros restantes tienen tipos idénticos a los de los parámetros correspondientes del método base.  
  
## Descripción de la regla  
 Un método de un tipo base está oculto por un método del mismo nombre en un tipo derivado, cuando la firma del parámetro del método derivado sólo se diferencia por tipos derivados de manera más débil que los tipos correspondientes de la firma del parámetro del método base.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite el método o cámbiele el nombre, o bien cambie la firma del parámetro de modo que el método no oculte el método base.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El siguiente ejemplo muestra un método que infringe la regla.  
  
 [!code-cs[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]