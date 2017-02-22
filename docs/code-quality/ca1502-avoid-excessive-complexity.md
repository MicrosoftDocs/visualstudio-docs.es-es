---
title: "CA1502: Evite la excesiva complejidad | Microsoft Docs"
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
  - "AvoidExcessiveComplexity"
  - "CA1502"
helpviewer_keywords: 
  - "CA1502"
  - "AvoidExcessiveComplexity"
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1502: Evite la excesiva complejidad
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveComplexity|  
|Identificador de comprobación|CA1502|  
|Categoría|Microsoft.Maintainability|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un método tiene una complejidad ciclomática excesiva.  
  
## Descripción de la regla  
 La *Complejidad ciclomática* mide el número de rutas de acceso independientes de forma lineal a través del método, que es determinado por el número y la complejidad de bifurcaciones condicionales.  Una complejidad ciclomática baja generalmente indica un método que es fácil de entender, comprobar y mantener.  La complejidad ciclomática se calcula a partir de un gráfico de flujo de control del método y se proporciona como:  
  
 complejidad ciclomática \= número de bordes \- número de nodos \+ 1  
  
 donde un nodo representa un punto de la bifurcación lógica y un borde representa una línea entre los nodos.  
  
 La regla notifica una infracción cuando la complejidad ciclomática es mayor de 25.  
  
 Puede obtener más información sobre métricas de código en [Medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, refactorice el método para reducir su complejidad ciclomática.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si la complejidad no se puede reducir fácilmente y el método es sencillo de entender, comprobar y mantener.  En particular, un método que contiene una instrucción `switch` grande \(`Select` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) es un candidato a la exclusión.  El riesgo de desestabilizar el código base al final del ciclo de desarrollo o incluir un cambio no esperado en el comportamiento en tiempo de ejecución en un código previamente distribuido, podría compensar las ventajas de mantenimiento de refactorización del código.  
  
## Cómo se calcula la complejidad ciclomática  
 La complejidad ciclomática se calcula sumando 1 a lo siguiente:  
  
-   Número de bifurcaciones \(como `if`, `while` y `do`\)  
  
-   El número de instrucciones `case` en `switch`  
  
 En los ejemplos siguientes se muestran métodos con distintas complejidades ciclomáticas.  
  
## Ejemplo  
 **Complejidad ciclomática de 1**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_1.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_1.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_1.cs)]  
  
## Ejemplo  
 **Complejidad ciclomática de 2**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_2.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_2.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_2.cs)]  
  
## Ejemplo  
 **Complejidad ciclomática de 3**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_3.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_3.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_3.cs)]  
  
## Ejemplo  
 **Complejidad ciclomática de 8**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_4.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_4.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_4.cs)]  
  
## Reglas relacionadas  
 [CA1501: Evite una herencia excesiva](../code-quality/ca1501-avoid-excessive-inheritance.md)  
  
## Vea también  
 [Medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)