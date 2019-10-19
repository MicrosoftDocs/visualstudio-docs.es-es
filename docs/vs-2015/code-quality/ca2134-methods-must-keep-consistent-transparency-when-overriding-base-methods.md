---
title: 'CA2134: los métodos deben mantener una transparencia coherente al invalidar los métodos base | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 96910ffc53e6c48f930232c83d87570f1bc71e00
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72608920"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: Los métodos deben mantener una transparencia coherente cuando reemplazan métodos base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 Esta regla se desencadena en los intentos de cambiar la accesibilidad de seguridad de un método más allá de la cadena de herencia. Por ejemplo, si un método virtual de una clase base es transparente o crítico para la seguridad, la clase derivada debe reemplazarlo con un método transparente o crítico para la seguridad. Por el contrario, si el virtual es crítico para la seguridad, la clase derivada debe reemplazarlo por un método crítico para la seguridad. La misma regla se aplica a la implementación de métodos de interfaz.

 Las reglas de transparencia se aplican cuando se compila el código JIT en lugar de hacerlo en tiempo de ejecución, de modo que el cálculo de transparencia no tiene información de tipo dinámico. Por consiguiente, el resultado del cálculo de transparencia debe poder determinarse únicamente a partir de los tipos estáticos que se van a compilar con JIT, independientemente del tipo dinámico.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie la transparencia del método que invalide un método virtual o implemente una interfaz para que coincida con la transparencia del método virtual o de la interfaz.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Las infracciones de esta regla producirán un <xref:System.TypeLoadException> en tiempo de ejecución para los ensamblados que usan la transparencia de nivel 2.

## <a name="examples"></a>Ejemplos

### <a name="code"></a>Código
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2134.methodsmustoverridewithconsistenttransparency/cs/ca2134 - methodsmustoverridewithconsistenttransparency.cs#1)]

## <a name="see-also"></a>Vea también
 [Código transparente en seguridad, nivel 2](https://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)
