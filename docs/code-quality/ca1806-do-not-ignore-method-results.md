---
title: 'CA1806: No omitir resultados del método'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
author: gewarren
ms.author: gewarren
dev_langs:
- CPP
- CSharp
- VB
manager: douge
ms.openlocfilehash: 865c4d26758021b0f0200f7834d02cd34f22bc8a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53954203"
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

- Se crea un nuevo objeto pero no se usa nunca.

- Se llama a un método que crea y devuelve una nueva cadena y nunca se usa la nueva cadena.

- Un método COM o P/Invoke que devuelve un código de error o HRESULT que nunca se utiliza. Descripción de la regla

Creación de objetos innecesarios y la recolección asociada del objeto sin usar degradar el rendimiento.

Las cadenas son inmutables y métodos como métodos String.ToUpper devuelve una nueva instancia de una cadena en lugar de modificar la instancia de la cadena del método de llamada.

Se omite el código de error o HRESULT puede producir un comportamiento inesperado en condiciones de error o a condiciones de recursos insuficientes.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Si un método crea una nueva instancia del objeto B que nunca se utiliza, pase la instancia como un argumento a otro método o asigne la instancia a una variable. Si la creación del objeto no es necesario, quítela.- o -

 Si un método llama al método B, pero no utiliza la nueva instancia de cadena que devuelve el método B. Pase la instancia como un argumento a otro método, asigne la instancia a una variable. O quite la llamada si no es necesaria.

 O bien

 Si un método llama al método B, pero no utiliza el valor HRESULT o código de error que devuelve el método. Use el resultado en una instrucción condicional, asigne el resultado a una variable o páselo como argumento a otro método.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima una advertencia de esta regla a menos que la acción de crear el objeto sirve para algún propósito.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra una clase que omite el resultado de String.Trim que realiza la llamada.

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_1.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_1.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_1.cpp)]

## <a name="example"></a>Ejemplo
 El ejemplo siguiente corrige la infracción anterior asignando el resultado de String.Trim a la variable que se llamó.

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_2.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_2.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_2.cpp)]

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un método que no utiliza un objeto que crea.

> [!NOTE]
> No se puede reproducir esta infracción en Visual Basic.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_3.cpp)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_3.cs)]

## <a name="example"></a>Ejemplo
 El ejemplo siguiente corrige la infracción anterior quitando la creación innecesaria de un objeto.

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_4.cs)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_4.cpp)]

<!-- Examples don't exist for the below... -->
<!--
## Example
 The following example shows a method that ignores the error code that the native method GetShortPathName returns.

## Example
 The following example fixes the previous violation by checking the error code and throwing an exception when the call fails.
-->