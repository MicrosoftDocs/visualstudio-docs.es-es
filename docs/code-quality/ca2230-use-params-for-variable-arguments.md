---
title: "CA2230: Usar par&#225;metros para argumentos de variable | Microsoft Docs"
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
  - "UseParamsForVariableArguments"
  - "CA2230"
helpviewer_keywords: 
  - "CA2230"
  - "UseParamsForVariableArguments"
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2230: Usar par&#225;metros para argumentos de variable
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseParamsForVariableArguments|  
|Identificador de comprobación|CA2230|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo público o protegido contiene un método público o protegido que utiliza la convención de llamada `VarArgs`.  
  
## Descripción de la regla  
 La convención de llamada `VarArgs` se utiliza con determinadas definiciones de método que toman un número variable de parámetros.  Un método que utiliza la convención de llamada `VarArgs` no es compatible con la Common Language Specification \(CLS\) y podría no ser accesible para todos los lenguajes de programación.  
  
 En C\#, se utiliza la convención de llamada `VarArgs` cuando la lista de parámetros del método termina con la palabra clave `__arglist`.  Visual Basic no admite la convención de llamada `VarArgs` y Visual C\+\+ permiten su uso sólo en código no administrado con puntos suspensivos `...`.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla en C\#, utilice la palabra clave [params](/dotnet/csharp/language-reference/keywords/params) en lugar de `__arglist`.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El ejemplo siguiente muestra dos métodos, uno que infringe la regla y otra que la cumple.  
  
 [!code-cs[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]  
  
## Vea también  
 <xref:System.Reflection.CallingConventions?displayProperty=fullName>   
 [Independencia del lenguaje y componentes independientes del lenguaje](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)