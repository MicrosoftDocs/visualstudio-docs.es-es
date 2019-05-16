---
title: 'CA2119: Sellar los métodos que satisfacen las interfaces privadas | Documentos de Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 56b08d1b842e65e1c1c29a7409813c314cbf014d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687273"
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
 Un tipo público heredable proporciona una implementación de método reemplazable de una `internal` (`Friend` en Visual Basic) interfaz.

## <a name="rule-description"></a>Descripción de la regla
 Los métodos de interfaz tienen accesibilidad pública, que no se puede cambiar el tipo de implementación. Una interfaz interna crea un contrato que no está pensado para implementarse fuera del ensamblado que define la interfaz. Un tipo público que implemente un método de una interfaz interna con el `virtual` (`Overridable` en Visual Basic) modificador permite que el método que sea reemplazado por un tipo derivado que está fuera del ensamblado. Si un segundo tipo en el ensamblado de definición llama al método y espera un contrato solo para uso interno, comportamiento podría estar en peligro cuando, en su lugar, se ejecuta el método invalidado en el ensamblado externo. Esto crea una vulnerabilidad de seguridad.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, evitar que el método se invalide fuera del ensamblado utilizando uno de los siguientes:

- Convierta el tipo declarativo `sealed` (`NotInheritable` en Visual Basic).

- Cambie la accesibilidad del tipo declarativo para `internal` (`Friend` en Visual Basic).

- Quite todos los constructores públicos del tipo declarativo.

- Implemente el método sin utilizar el `virtual` modificador.

- Implementar el método de forma explícita.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si, tras una revisión exhaustiva, existe ningún problema de seguridad que puede ser aprovechable si se reemplaza el método fuera del ensamblado.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo, `BaseImplementation`, que infringe esta regla.

 [!code-cpp[FxCop.Security.SealMethods1#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cpp/FxCop.Security.SealMethods1.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cs/FxCop.Security.SealMethods1.cs#1)]
 [!code-vb[FxCop.Security.SealMethods1#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/vb/FxCop.Security.SealMethods1.vb#1)]

## <a name="example"></a>Ejemplo
 El ejemplo siguiente aprovecha la implementación del método virtual del ejemplo anterior.

 [!code-cpp[FxCop.Security.SealMethods2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cpp/FxCop.Security.SealMethods2.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cs/FxCop.Security.SealMethods2.cs#1)]
 [!code-vb[FxCop.Security.SealMethods2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/vb/FxCop.Security.SealMethods2.vb#1)]

## <a name="see-also"></a>Vea también
 [Interfaces](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37) [Interfaces](https://msdn.microsoft.com/library/61b06674-12c9-430b-be68-cc67ecee1f5b)
