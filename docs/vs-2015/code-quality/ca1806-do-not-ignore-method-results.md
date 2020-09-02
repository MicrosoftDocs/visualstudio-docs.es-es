---
title: 'CA1806: no omitir resultados del método | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 726cde42eb08ee5508481887fae2e9d2b059256c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543876"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806: No omitir resultados del método
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|DoNotIgnoreMethodResults|
|Identificador de comprobación|CA1806|
|Category|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 Hay varias razones posibles para esta ADVERTENCIA:

- Se crea un nuevo objeto, pero nunca se usa.

- Se llama a un método que crea y devuelve una nueva cadena y la nueva cadena nunca se utiliza.

- Un método COM o P/Invoke que devuelve un código de error o HRESULT que nunca se usa. Descripción de la regla

  La creación de objetos innecesarios y la recolección de elementos no utilizados asociada del objeto no usado degrada el rendimiento.

  Las cadenas son inmutables y los métodos como String. ToUpper devuelven una nueva instancia de una cadena en lugar de modificar la instancia de la cadena en el método de llamada.

  Si se omite el código de error o HRESULT, puede producirse un comportamiento inesperado en condiciones de error o en condiciones de recursos insuficientes.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Si el método A crea una nueva instancia del objeto B que nunca se utiliza, pase la instancia como un argumento a otro método o asigne la instancia a una variable. Si la creación del objeto es innecesaria, quítela.-o-

 Si el método A llama al método B, pero no utiliza la nueva instancia de la cadena que devuelve el método B. Pase la instancia como un argumento a otro método, asigne la instancia a una variable. O quite la llamada si no es necesario.

 o bien

 Si el método A llama al método B, pero no usa el código de error o HRESULT que devuelve el método. Use el resultado en una instrucción condicional, asigne el resultado a una variable o páselo como un argumento a otro método.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima una advertencia de esta regla a menos que el acto de crear el objeto tenga algún propósito.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra una clase que omite el resultado de llamar a String. Trim.

<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  -->

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se corrige la infracción anterior asignando el resultado de String. Trim de nuevo a la variable en la que se llamó.

<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  -->

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un método que no utiliza un objeto que crea.

> [!NOTE]
> Esta infracción no se puede reproducir en Visual Basic.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cpp/FxCop.Usage.DoNotIgnoreMethodResults3.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cs/FxCop.Usage.DoNotIgnoreMethodResults3.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/vb/FxCop.Usage.DoNotIgnoreMethodResults3.vb#1)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se corrige la infracción anterior quitando la creación innecesaria de un objeto.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cpp/FxCop.Usage.DoNotIgnoreMethodResults4.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cs/FxCop.Usage.DoNotIgnoreMethodResults4.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/vb/FxCop.Usage.DoNotIgnoreMethodResults4.vb#1)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un método que omite el código de error que devuelve el método nativo GetShortPathName.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cpp/FxCop.Usage.DoNotIgnoreMethodResults5.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cs/FxCop.Usage.DoNotIgnoreMethodResults5.cs#1)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se corrige la infracción anterior comprobando el código de error y produciendo una excepción cuando se produce un error en la llamada.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cpp/FxCop.Usage.DoNotIgnoreMethodResults6.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cs/FxCop.Usage.DoNotIgnoreMethodResults6.cs#1)]