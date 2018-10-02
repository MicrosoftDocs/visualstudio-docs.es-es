---
title: 'CA1026: No se debería utilizar parámetros predeterminados | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2fab184cba9084dbcfa38ebb60aec53077900144
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47592336"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: No debería utilizar parámetros predeterminados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA1026: no se debería utilizar parámetros predeterminados](https://docs.microsoft.com/visualstudio/code-quality/ca1026-default-parameters-should-not-be-used).

|||
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|Identificador de comprobación|CA1026|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo visible externamente contiene un método visible externamente que utiliza un parámetro predeterminado.

## <a name="rule-description"></a>Descripción de la regla
 Se permiten los métodos que utilizan parámetros predeterminados en el Common Language Specification (CLS); Sin embargo, CLS permite que los compiladores omitan los valores que se asignan a estos parámetros. Código que se escribe para los compiladores omitan los valores de parámetro predeterminado debe proporcionar explícitamente los argumentos para cada parámetro predeterminado. Para mantener el comportamiento que desea en lenguajes de programación, se deben reemplazar los métodos que utilizan parámetros predeterminados con sobrecargas de método que proporcionan los parámetros predeterminados.

 Cuando tiene acceso a código administrado, el compilador omite los valores de parámetros predeterminados de extensión administrada de C++. El compilador de Visual Basic admite métodos que tienen parámetros predeterminados que usan el [opcional](http://msdn.microsoft.com/library/4571ce88-a539-4115-b230-54eb277c6aa7) palabra clave.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, reemplace el método que utiliza los parámetros predeterminados con sobrecargas de método que proporcionan los parámetros predeterminados.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un método que utiliza los parámetros predeterminados y los métodos sobrecargados que proporcionan una funcionalidad equivalente.

 [!code-vb[FxCop.Design.DefaultParameters#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DefaultParameters/vb/FxCop.Design.DefaultParameters.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1025: Reemplaza argumentos repetitivos con una matriz de parámetros](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>Vea también
 [Independencia del lenguaje y componentes independientes del lenguaje](http://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)



