---
title: "CA2200: Iniciar de nuevo para preservar los detalles de la pila | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RethrowToPreserveStackDetails"
  - "CA2200"
helpviewer_keywords: 
  - "CA2200"
  - "RethrowToPreserveStackDetails"
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2200: Iniciar de nuevo para preservar los detalles de la pila
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|RethrowToPreserveStackDetails|  
|Identificador de comprobación|CA2200|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Se vuelve a producir una excepción y se especifica explícitamente en la instrucción `throw`.  
  
## Descripción de la regla  
 Cuando se produce una excepción, la parte de la información que lleva es el seguimiento de pila.  El seguimiento de pila es una lista de la jerarquía de llamadas al método que comienza con el método que produce la excepción y finaliza con el que detecta la excepción.  Si se vuelve a producir una excepción especificándola en la instrucción `throw`, el seguimiento de pila se reinicia en el método actual y se pierde la lista de llamadas al método entre el método original que produjo la excepción y el método actual.  Para mantener la información del seguimiento de pila original con la excepción, utilice la instrucción `throw` sin especificar la excepción.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, vuelva a producir la excepción sin especificarla explícitamente.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El ejemplo siguiente muestra un método, `CatchAndRethrowExplicitly`, que infringe la regla y un método, `CatchAndRethrowImplicitly`, que cumple la regla.  
  
 [!code-cs[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/CSharp/ca2200-rethrow-to-preserve-stack-details_1.cs)]
 [!code-vb[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/VisualBasic/ca2200-rethrow-to-preserve-stack-details_1.vb)]