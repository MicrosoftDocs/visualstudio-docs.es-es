---
title: "Se han usado operandos del tipo Object para el operador &#39;&lt;operatorsymbol&gt;&#39;. Use el operador &#39;Is&#39; para comprobar la identidad del objeto. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42018"
  - "BC42018"
helpviewer_keywords: 
  - "BC42018"
ms.assetid: 3fc640a7-7dab-4c14-b25d-a5794dbba59d
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se han usado operandos del tipo Object para el operador &#39;&lt;operatorsymbol&gt;&#39;. Use el operador &#39;Is&#39; para comprobar la identidad del objeto.
Una expresión usa el `=` con uno o ambos operandos de [Object \(Tipo de datos\)](/dotnet/visual-basic/language-reference/data-types/object-data-type).  
  
 Debe usar el operador `Is` o `IsNot` para determinar si dos referencias de objeto hacen referencia a la misma instancia de objeto. Vea "Comparar objetos" en [Operadores de comparación en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators).  
  
 Cuando una variable o expresión se evalúa como `Object`, el compilador debe realizar el  *enlace tardío*, que produce operaciones adicionales en tiempo de ejecución. También expone la aplicación a posibles errores en tiempo de ejecución. Por ejemplo, si asigna un <xref:System.Windows.Forms.Form> a una variable `Object` e intenta usarlo con el operador `=`, el runtime produce una <xref:System.InvalidCastException> porque Visual Basic no puede convertir un objeto <xref:System.Windows.Forms.Form> a un tipo de datos adecuado para la comparación de valores. Incluso si ambos operandos se evalúan en el tipo <xref:System.Windows.Forms.Form>, se produce un error en la operación porque `=` no está definido para operandos <xref:System.Windows.Forms.Form>.  
  
 De forma predeterminada, este mensaje es una advertencia. Para más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC42018  
  
### Para corregir este error  
  
-   Para determinar si dos referencias de objeto hacen referencia a la misma instancia de objeto, use el operador `Is` o `IsNot`.  
  
## Vea también  
 [Operadores de comparación en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)   
 [Is \(Operador\)](/dotnet/visual-basic/language-reference/operators/is-operator)   
 [Cómo: Determinar si dos objetos están relacionados](../Topic/How%20to:%20Determine%20Whether%20Two%20Objects%20Are%20Related%20\(Visual%20Basic\).md)   
 [Cómo: Determinar si dos objetos son idénticos](../Topic/How%20to:%20Determine%20Whether%20Two%20Objects%20Are%20Identical%20\(Visual%20Basic\).md)