---
title: 'CA1806: No omitir resultados del método | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5d28ca688bbad0054f7522034bfe309dcb1fe698
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49250112"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806: No omitir resultados del método
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotIgnoreMethodResults|  
|Identificador de comprobación|CA1806|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No trascendental|  
  
## <a name="cause"></a>Motivo  
 Hay varias razones posibles para esta advertencia:  
  
-   Se crea un nuevo objeto pero no se usa nunca.  
  
-   Se llama a un método que crea y devuelve una nueva cadena y nunca se usa la nueva cadena.  
  
-   Un método COM o P/Invoke que devuelve un código de error o HRESULT que nunca se utiliza. Descripción de la regla  
  
 Creación de objetos innecesarios y la recolección asociada del objeto sin usar degradar el rendimiento.  
  
 Las cadenas son inmutables y métodos como métodos String.ToUpper devuelve una nueva instancia de una cadena en lugar de modificar la instancia de la cadena del método de llamada.  
  
 Se omite el código de error o HRESULT puede producir un comportamiento inesperado en condiciones de error o a condiciones de recursos insuficientes.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Si un método crea una nueva instancia del objeto B que nunca se utiliza, pase la instancia como un argumento a otro método o asigne la instancia a una variable. Si la creación del objeto no es necesario, quítela.- o -  
  
 Si un método llama al método B, pero no utiliza la nueva instancia de cadena que devuelve el método B. Pase la instancia como un argumento a otro método, asigne la instancia a una variable. O quite la llamada si no es necesaria.  
  
 O bien  
  
 Si un método llama al método B, pero no utiliza el valor HRESULT o código de error que devuelve el método. Use el resultado en una instrucción condicional, asigne el resultado a una variable o páselo como argumento a otro método.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima una advertencia de esta regla a menos que la acción de crear el objeto sirve para algún propósito.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra una clase que omite el resultado de String.Trim que realiza la llamada.  
  
<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  -->  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente corrige la infracción anterior asignando el resultado de String.Trim a la variable que se llamó.  
  
<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  -->  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra un método que no utiliza un objeto que crea.  
  
> [!NOTE]
>  No se puede reproducir esta infracción en Visual Basic.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cpp/FxCop.Usage.DoNotIgnoreMethodResults3.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cs/FxCop.Usage.DoNotIgnoreMethodResults3.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/vb/FxCop.Usage.DoNotIgnoreMethodResults3.vb#1)]  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente corrige la infracción anterior quitando la creación innecesaria de un objeto.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cpp/FxCop.Usage.DoNotIgnoreMethodResults4.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cs/FxCop.Usage.DoNotIgnoreMethodResults4.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/vb/FxCop.Usage.DoNotIgnoreMethodResults4.vb#1)]  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra un método que pasa por alto el código de error que devuelve el método nativo GetShortPathName.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cpp/FxCop.Usage.DoNotIgnoreMethodResults5.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cs/FxCop.Usage.DoNotIgnoreMethodResults5.cs#1)]  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente corrige la infracción anterior, compruebe el código de error y producir una excepción cuando se produce un error en la llamada.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cpp/FxCop.Usage.DoNotIgnoreMethodResults6.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cs/FxCop.Usage.DoNotIgnoreMethodResults6.cs#1)]