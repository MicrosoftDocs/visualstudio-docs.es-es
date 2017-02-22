---
title: "CA2241: Proporcionar argumentos correctos para los m&#233;todos de formato | Microsoft Docs"
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
  - "CA2241"
  - "Provide correct arguments to formatting methods"
  - "ProvideCorrectArgumentsToFormattingMethods"
helpviewer_keywords: 
  - "CA2241"
  - "ProvideCorrectArgumentsToFormattingMethods"
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2241: Proporcionar argumentos correctos para los m&#233;todos de formato
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ProvideCorrectArgumentsToFormattingMethods|  
|Identificador de comprobación|CA2241|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 El argumento de cadena `format` pasado a un método como <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> o <xref:System.String.Format%2A?displayProperty=fullName> no contiene un elemento de formato que corresponda a cada argumento de objeto o viceversa.  
  
## Descripción de la regla  
 Los argumentos de métodos como <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> y <xref:System.String.Format%2A> constan de una cadena de formato seguida de varias instancias de <xref:System.Object?displayProperty=fullName>.  La cadena de formato está compuesta de texto y elementos de formato del formulario incrustados, {index\[,alignment\]\[:formatString\]}. “los índices son un entero cero\- basado en que indica cuál de los objetos al formato.  Si un objeto no tiene un índice correspondiente en la cadena de formato, se omite el objeto.  Si el objeto especificado por 'index' no existe, <xref:System.FormatException?displayProperty=fullName> se produce en tiempo de ejecución.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, proporcione un elemento de formato para cada argumento de objeto y proporcione un argumento de objeto para cada elemento de formato.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El ejemplo siguiente muestra dos infracciones de esta regla.  
  
 [!code-vb[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/VisualBasic/ca2241-provide-correct-arguments-to-formatting-methods_1.vb)]
 [!code-cs[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/CSharp/ca2241-provide-correct-arguments-to-formatting-methods_1.cs)]