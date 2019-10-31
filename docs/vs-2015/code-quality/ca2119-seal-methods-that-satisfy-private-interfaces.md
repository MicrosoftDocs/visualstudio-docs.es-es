---
title: 'CA2119: Sellar los métodos que satisfacen las interfaces privadas | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: af41fc5576cbcd56589680d99c0cd5c0dfd6e6f1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664767"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119: Sellar los métodos que satisfacen las interfaces privadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|Identificador de comprobación|CA2119|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo público heredable proporciona una implementación de método reemplazable de una interfaz `internal` (`Friend` en Visual Basic).

## <a name="rule-description"></a>Descripción de la regla
 Los métodos de interfaz tienen accesibilidad pública, que el tipo de implementación no puede cambiar. Una interfaz interna crea un contrato que no está diseñado para implementarse fuera del ensamblado que define la interfaz. Un tipo público que implementa un método de una interfaz interna mediante el modificador `virtual` (`Overridable` en Visual Basic) permite que un tipo derivado que está fuera del ensamblado invalide el método. Si un segundo tipo del ensamblado de definición llama al método y espera un contrato solo interno, el comportamiento puede verse comprometido cuando, en su lugar, se ejecuta el método invalidado en el ensamblado externo. Esto crea una vulnerabilidad de seguridad.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, evite que el método se invalide fuera del ensamblado mediante una de las siguientes acciones:

- Haga que el tipo declarativo `sealed` (`NotInheritable` en Visual Basic).

- Cambie la accesibilidad del tipo declarativo a `internal` (`Friend` en Visual Basic).

- Quite todos los constructores públicos del tipo declarativo.

- Implemente el método sin usar el modificador `virtual`.

- Implemente el método explícitamente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si, después de una revisión cuidadosa, no existe ningún problema de seguridad que pueda ser aprovechable si el método se invalida fuera del ensamblado.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo, `BaseImplementation`, que infringe esta regla.

 [!code-cpp[FxCop.Security.SealMethods1#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cpp/FxCop.Security.SealMethods1.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cs/FxCop.Security.SealMethods1.cs#1)]
 [!code-vb[FxCop.Security.SealMethods1#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/vb/FxCop.Security.SealMethods1.vb#1)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se aprovecha la implementación del método virtual del ejemplo anterior.

 [!code-cpp[FxCop.Security.SealMethods2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cpp/FxCop.Security.SealMethods2.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cs/FxCop.Security.SealMethods2.cs#1)]
 [!code-vb[FxCop.Security.SealMethods2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/vb/FxCop.Security.SealMethods2.vb#1)]

## <a name="see-also"></a>Vea también
 [Interfaces](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37) [Interfaces](https://msdn.microsoft.com/library/61b06674-12c9-430b-be68-cc67ecee1f5b)
