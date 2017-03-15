---
title: "CA1804: Quitar variables locales no utilizadas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1804"
  - "RemoveUnusedLocals"
helpviewer_keywords: 
  - "RemoveUnusedLocals"
  - "CA1804"
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1804: Quitar variables locales no utilizadas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|RemoveUnusedLocals|  
|Identificador de comprobación|CA1804|  
|Categoría|Microsoft.Performance|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un método declara una variable local pero no utiliza la variable excepto en algunos casos como el destinatario de una instrucción de asignación.  Para obtener un análisis mediante esta regla, el ensamblado probado se debe compilar con información de depuración y el archivo de base de datos de programa asociado \(.pdb\) debe estar disponible.  
  
## Descripción de la regla  
 Las variables locales no usadas y las asignaciones innecesarias aumentan el tamaño de un ensamblado y reducen el rendimiento.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite o utilice la variable local.  Observe que el compilador de C\# incluido con [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] quita estas variables locales innecesarias cuando se habilita la opción `optimize`.  
  
## Cuándo suprimir advertencias  
 Suprima una advertencia de esta regla si la variable la generó el compilador.  También es seguro suprimir una advertencia de esta regla, o deshabilitar la regla, si el rendimiento y el mantenimiento de código no son prioritarios.  
  
## Ejemplo  
 El siguiente ejemplo muestra varias variables locales que no se utilizan.  
  
 [!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
 [!code-cs[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]  
  
## Reglas relacionadas  
 [CA1809: Evitar el exceso de variables locales](../code-quality/ca1809-avoid-excessive-locals.md)  
  
 [CA1811: Evitar código privado al que no se llama](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Evitar las clases internas sin instancia](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801: Revisar parámetros sin utilizar](../code-quality/ca1801-review-unused-parameters.md)