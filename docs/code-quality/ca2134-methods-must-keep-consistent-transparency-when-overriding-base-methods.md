---
title: 'CA2134: Los métodos deben mantener una transparencia coherente al invalidar métodos base'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ca28f364307d4a2b73235bc6541cb8aa01abd56
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920658"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: Los métodos deben mantener una transparencia coherente al invalidar métodos base

|||
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|Identificador de comprobación|CA2134|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Esta regla se desencadena cuando un método marcado con <xref:System.Security.SecurityCriticalAttribute> invalida un método que es transparente o está marcado <xref:System.Security.SecuritySafeCriticalAttribute>con. La regla también se desencadena cuando un método que es transparente o está marcado <xref:System.Security.SecuritySafeCriticalAttribute> con reemplaza un método marcado con un. <xref:System.Security.SecurityCriticalAttribute>

Se aplica la regla al invalidar un método virtual o implementar una interfaz.

## <a name="rule-description"></a>Descripción de la regla
Esta regla se desencadena en los intentos de cambiar la accesibilidad de seguridad de un método más allá de la cadena de herencia. Por ejemplo, si un método virtual de una clase base es transparente o crítico para la seguridad, la clase derivada debe reemplazarlo con un método transparente o crítico para la seguridad. Por el contrario, si el virtual es crítico para la seguridad, la clase derivada debe reemplazarlo por un método crítico para la seguridad. La misma regla se aplica a la implementación de métodos de interfaz.

Las reglas de transparencia se aplican cuando se compila el código JIT en lugar de hacerlo en tiempo de ejecución, de modo que el cálculo de transparencia no tiene información de tipo dinámico. Por consiguiente, el resultado del cálculo de transparencia debe poder determinarse únicamente a partir de los tipos estáticos que se van a compilar con JIT, independientemente del tipo dinámico.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, cambie la transparencia del método que invalide un método virtual o implemente una interfaz para que coincida con la transparencia del método virtual o de la interfaz.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla. Las infracciones de esta regla darán lugar <xref:System.TypeLoadException> a un tiempo de ejecución para los ensamblados que usan la transparencia de nivel 2.

## <a name="examples"></a>Ejemplos

### <a name="code"></a>Código
[!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods_1.cs)]

## <a name="see-also"></a>Vea también
[Código transparente en seguridad, nivel 2](/dotnet/framework/misc/security-transparent-code-level-2)