---
title: "CA1026: No deber&#237;a utilizar par&#225;metros predeterminados | Microsoft Docs"
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
  - "CA1026"
  - "DefaultParametersShouldNotBeUsed"
helpviewer_keywords: 
  - "CA1026"
  - "DefaultParametersShouldNotBeUsed"
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1026: No deber&#237;a utilizar par&#225;metros predeterminados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DefaultParametersShouldNotBeUsed|  
|Identificador de comprobación|CA1026|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo visible externamente contiene un método visible externamente que utiliza un parámetro predeterminado.  
  
## Descripción de la regla  
 Los métodos que utilizan parámetros predeterminados están permitidos en Common Language Specification \(CLS\); sin embargo, la CLS permite que los compiladores omitan los valores asignados a estos parámetros.  El código escrito para que los compiladores omitan los valores de parámetro predeterminado debe proporcionar explícitamente los argumentos para cada parámetro predeterminado.  Para seguir utilizando el comportamiento que desea en los lenguajes de programación, los métodos que utilizan parámetros predeterminados deberían reemplazarse con sobrecargas de métodos que proporcionen los parámetros predeterminados.  
  
 El compilador omite los valores de los parámetros predeterminados de Extensión administrada para C\+\+ al obtener acceso al código administrado.  El compilador de Visual Basic admite métodos que tienen parámetros predeterminados que utilizan la palabra clave [Optional](/dotnet/visual-basic/language-reference/modifiers/optional).  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, reemplace el método que utiliza los parámetros predeterminados con sobrecargas de método que proporcionan los parámetros predeterminados.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El ejemplo siguiente muestra un método que utiliza los parámetros predeterminados y los métodos sobrecargados que proporcionan una funcionalidad equivalente.  
  
 [!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]  
  
## Reglas relacionadas  
 [CA1025: Reemplaza argumentos repetitivos con una matriz de parámetros](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)  
  
## Vea también  
 [Independencia del lenguaje y componentes independientes del lenguaje](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)