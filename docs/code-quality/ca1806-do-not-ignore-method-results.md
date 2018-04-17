---
title: 'CA1806: No omitir resultados del método | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 90908bb85d88d939e2886f60083c0499cde2823c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806: No omitir resultados del método
|||  
|-|-|  
|TypeName|DoNotIgnoreMethodResults|  
|Identificador de comprobación|CA1806|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No trascendental|  
  
## <a name="cause"></a>Motivo  
 Hay varias razones posibles para esta advertencia:  
  
-   Un nuevo objeto se crea pero nunca se utiliza.  
  
-   Se llama a un método que crea y devuelve una nueva cadena y la nueva cadena nunca se utiliza.  
  
-   Un método COM o P/Invoke que devuelve un código de error o HRESULT que nunca se utiliza. Descripción de la regla  
  
 Creación de objetos innecesarios y la recolección asociado del objeto sin usar degradar el rendimiento.  
  
 Las cadenas son inmutables y métodos como métodos String.ToUpper devuelve una nueva instancia de una cadena en lugar de modificar la instancia de la cadena en el método de llamada.  
  
 Se omitirá el código de error o HRESULT puede producir un comportamiento inesperado en condiciones de error o a las condiciones de recursos insuficientes.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Si un método crea una nueva instancia del objeto B que nunca se utiliza, pase la instancia como un argumento a otro método o asigne la instancia a una variable. Si la creación del objeto es innecesaria, quítela.- o -  
  
 Si un método llama al método B pero no utiliza la nueva instancia de cadena que devuelve el método B. Pase la instancia como un argumento a otro método, asigne la instancia a una variable. O bien, quite la llamada si no es necesario.  
  
 -o bien-  
  
 Si un método llama al método B pero no utiliza el valor HRESULT o código de error que devuelve el método. Utilizar el resultado en una instrucción condicional, asigne el resultado a una variable o páselo como argumento a otro método.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla a menos que la acción de crear el objeto tiene algunos finalidad.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra una clase que omite el resultado de String.Trim que realiza la llamada.  
  
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_1.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_1.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_1.cpp)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se corrige la infracción anterior asignando el resultado de String.Trim a la variable que se llamó en.  
  
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_2.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_2.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_2.cpp)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un método que no utiliza un objeto que crea.  
  
> [!NOTE]
>  Esta infracción no se puede reproducir en Visual Basic.  

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_3.cpp)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_3.cs)]   
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se corrige la infracción anterior quitando la creación innecesaria de un objeto.  

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_4.cs)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_4.cpp)] 

<!-- Examples don't exist for the below... -->
<!--
## Example  
 The following example shows a method that ignores the error code that the native method GetShortPathName returns.  
  
## Example  
 The following example fixes the previous violation by checking the error code and throwing an exception when the call fails.  
-->