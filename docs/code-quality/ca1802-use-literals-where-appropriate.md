---
title: "CA1802: Usar literales cuando resulte apropiado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseLiteralsWhereAppropriate"
  - "CA1802"
helpviewer_keywords: 
  - "UseLiteralsWhereAppropriate"
  - "CA1802"
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1802: Usar literales cuando resulte apropiado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseLiteralsWhereAppropriate|  
|Identificador de comprobación|CA1802|  
|Categoría|Microsoft.Performance|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Se declara un campo `static` y `readonly` \(`Shared` y `ReadOnly` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) y se inicializa con un valor que se puede calcular durante la compilación.  
  
## Descripción de la regla  
 El valor de un campo  `static` `readonly` se calcula en tiempo de ejecución cuando se llama al constructor estático correspondiente al tipo declarativo.  Si el campo `static` `readonly` se inicializa cuando se declara y no se declara un constructor estático de manera explícita, el compilador emite un constructor estático para inicializar el campo.  
  
 El valor de un campo `const` se calcula en tiempo de compilación y se almacena en los metadatos, lo que aumenta el rendimiento en tiempo de ejecución en comparación con un campo `static` `readonly`.  
  
 Dado que el valor asignado al campo de destino se calcula en tiempo de compilación, cambie la declaración a un campo `const` para que el valor se calcule en tiempo de compilación en lugar de en tiempo de ejecución.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, reemplace los modificadores `static` y `readonly` por el modificador `const`.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla o deshabilitar la regla, si el rendimiento no es importante.  
  
## Ejemplo  
 El ejemplo siguiente muestra un tipo \(`UseReadOnly`\) que infringe la regla y otro \(`UseConstant`\) que la cumple.  
  
 [!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
 [!code-cs[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]