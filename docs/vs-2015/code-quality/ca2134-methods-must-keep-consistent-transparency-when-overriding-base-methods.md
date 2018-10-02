---
title: 'CA2134: Los métodos deben mantener una transparencia coherente cuando reemplazan métodos base | Microsoft Docs'
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
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: df04e5462e2b03c402ce792b390b476b05873036
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591595"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: Los métodos deben mantener una transparencia coherente cuando reemplazan métodos base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA2134: los métodos deben mantener una transparencia coherente cuando reemplazan métodos base](https://docs.microsoft.com/visualstudio/code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods).

|||
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|Identificador de comprobación|CA2134|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Esta regla se desencadena cuando un método marcado con el <xref:System.Security.SecurityCriticalAttribute> invalida un método que es transparente o está marcado con el <xref:System.Security.SecuritySafeCriticalAttribute>. La regla también se desencadena cuando un método que es transparente o está marcado con el <xref:System.Security.SecuritySafeCriticalAttribute> invalida un método marcado con un <xref:System.Security.SecurityCriticalAttribute>.

 Se aplica la regla al invalidar un método virtual o implementar una interfaz.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla se desencadena en los intentos de cambiar la accesibilidad de seguridad de un método más arriba la cadena de herencia. Por ejemplo, si un método virtual en una clase base es transparente o crítico para la seguridad, la clase derivada debe invalidarlo con un método transparente o crítico para la seguridad. Por el contrario, si el virtual es crítico para la seguridad, la clase derivada debe reemplazar con un método crítico de seguridad. Se aplica la misma regla para implementar los métodos de interfaz.

 Las reglas de transparencia se aplican cuando el código está compilado en lugar de en tiempo de ejecución, de forma JIT para que el cálculo de transparencia no tiene información de tipo dinámico. Por lo tanto, el resultado del cálculo de transparencia debe poder determinar únicamente a partir de los tipos estáticos que se va a la compilación JIT, independientemente del tipo dinámico.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie la transparencia del método que se reemplace un método virtual o implementar una interfaz para que coincida con la transparencia de la memoria virtual o el método de interfaz.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Las infracciones de esta regla dará como resultado un tiempo de ejecución <xref:System.TypeLoadException> para ensamblados que utilizan la transparencia de nivel 2.

## <a name="examples"></a>Ejemplos

### <a name="code"></a>Código
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2134.methodsmustoverridewithconsistenttransparency/cs/ca2134 - methodsmustoverridewithconsistenttransparency.cs#1)]

## <a name="see-also"></a>Vea también
 [Código transparente en seguridad, nivel 2](http://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)



