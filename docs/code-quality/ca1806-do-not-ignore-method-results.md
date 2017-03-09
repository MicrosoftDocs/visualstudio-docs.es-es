---
title: "CA1806: No omitir resultados del m&#233;todo | Microsoft Docs"
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
  - "CA1806"
  - "DoNotIgnoreMethodResults"
helpviewer_keywords: 
  - "CA1806"
  - "DoNotIgnoreMethodResults"
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1806: No omitir resultados del m&#233;todo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotIgnoreMethodResults|  
|Identificador de comprobación|CA1806|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Hay varios motivos posibles para esta advertencia.  
  
-   Se creó un objeto nuevo pero nunca se utilizó.  
  
-   Se llama a un método que crea y devuelve una cadena nueva y la nueva cadena nunca se utiliza.  
  
-   Un método COM o P\/Invoke devuelve un código de error o HRESULT que nunca se utiliza.  Descripción de la regla  
  
 La creación innecesaria de objetos y la recolección de elementos no utilizados asociada al objeto no utilizado reducen el rendimiento.  
  
 Las cadenas son inmutables y métodos como String.ToUpper devuelven una nueva instancia de una cadena en lugar de modificar la instancia de la cadena en el método de llamada.  
  
 La omisión de un código de error o HRESULT puede producir un comportamiento inesperado en situaciones de error o de escasez de recursos.  
  
## Cómo corregir infracciones  
 Si el método A crea una nueva instancia del objeto B que nunca se utiliza, pase la instancia como argumento a otro método o asigne la instancia a una variable.  Si la creación del objeto no es necesaria, quítela. \-O bien\-  
  
 Si el método A llama al método B pero no utiliza la nueva instancia de la cadena devuelta por el método B,  pase la instancia como argumento a otro método, asigne la instancia a una variable  o quite la llamada si no es necesaria.  
  
 O bien  
  
 Si el método A llama al método B pero no utiliza el código de error o HRESULT devuelto por el método B,  Use el resultado en una instrucción condicional, asigne el resultado a una variable o páselo como un argumento a otro método.  
  
## Cuándo suprimir advertencias  
 No suprima ninguna advertencia de esta regla a menos que la creación del objeto sirva para algún propósito.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra una clase que omite el resultado de la llamada a String.Trim.  
  
 [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  
  
## Ejemplo  
 En el ejemplo siguiente se corrige la infracción anterior asignando de nuevo el resultado de String.Trim a la variable en la que se realizó la llamada.  
  
 [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  
  
## Ejemplo  
 En el ejemplo siguiente se muestra un método que no utiliza ningún objeto de los que crea.  
  
> [!NOTE]
>  Esta infracción no puede reproducirse en Visual Basic.  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_1.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_1.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_1.cpp)]  
  
## Ejemplo  
 En el ejemplo siguiente se corrige la infracción anterior quitando la creación innecesaria de un objeto.  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_2.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_2.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_2.cpp)]  
  
## Ejemplo  
 En el ejemplo siguiente se muestra un método que omite el código de error que el método nativo GetShortPathName devuelve.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_3.cpp)]
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_3.cs)]  
  
## Ejemplo  
 En el ejemplo siguiente se corrige la infracción anterior comprobando el código de error e iniciando una excepción si la llamada no se realiza correctamente.  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_4.cs)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_4.cpp)]