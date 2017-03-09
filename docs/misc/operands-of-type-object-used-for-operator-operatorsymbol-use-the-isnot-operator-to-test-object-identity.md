---
title: "Se usaron operandos de tipo Object para el operador &#39;&lt;s&#237;mboloDeOperador&gt;&#39;; use el operador &#39;IsNot&#39; para comprobar la identidad del objeto | Microsoft Docs"
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
  - "vbc42032"
  - "bc42032"
helpviewer_keywords: 
  - "BC42032"
ms.assetid: f43b163b-f8f6-489d-ba9e-df6398ccc553
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se usaron operandos de tipo Object para el operador &#39;&lt;s&#237;mboloDeOperador&gt;&#39;; use el operador &#39;IsNot&#39; para comprobar la identidad del objeto
Una expresión usa el operador `<>` con uno o ambos operandos de [Object \(Tipo de datos\)](/dotnet/visual-basic/language-reference/data-types/object-data-type).  
  
 Debe usar el operador `Is` o `IsNot` para determinar si dos referencias de objeto hacen referencia a la misma instancia de objeto. Vea "Comparar objetos" en [Operadores de comparación en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators).  
  
 Si una variable o expresión se evalúa como `Object`, el compilador debe realizar el *enlace en tiempo de ejecución*, que produce operaciones adicionales en tiempo de ejecución. También expone la aplicación a posibles errores en tiempo de ejecución. Por ejemplo, si asigna un <xref:System.Windows.Forms.Form> a una variable `Object` e intenta usarlo con el operador `<>`, el tiempo de ejecución inicia una <xref:System.InvalidCastException> porque Visual Basic no puede convertir un objeto <xref:System.Windows.Forms.Form> a un tipo de datos adecuado para la comparación de valores. Aunque ambos operandos se evalúen como el tipo <xref:System.Windows.Forms.Form>, se produce un error en la operación porque `<>` no está definido para operandos <xref:System.Windows.Forms.Form>.  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC42032  
  
### Para corregir este error  
  
-   Para determinar si dos referencias de objeto hacen referencia a la misma instancia de objeto, use el operador `Is` o `IsNot`.  
  
## Vea también  
 [Operadores de comparación en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)   
 [IsNot \(Operador\)](/dotnet/visual-basic/language-reference/operators/isnot-operator)   
 [Cómo: Determinar si dos objetos están relacionados](../Topic/How%20to:%20Determine%20Whether%20Two%20Objects%20Are%20Related%20\(Visual%20Basic\).md)   
 [Cómo: Determinar si dos objetos son idénticos](../Topic/How%20to:%20Determine%20Whether%20Two%20Objects%20Are%20Identical%20\(Visual%20Basic\).md)