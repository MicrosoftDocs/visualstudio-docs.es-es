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
ms.openlocfilehash: fe9a84280b0124eed6bb0cfffae9c1ec2942bddf
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547724"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: Los métodos deben mantener una transparencia coherente al invalidar métodos base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|Identificador de comprobación|CA2134|
|Category|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Esta regla se desencadena cuando un método marcado con <xref:System.Security.SecurityCriticalAttribute> invalida un método que es transparente o está marcado con <xref:System.Security.SecuritySafeCriticalAttribute> . La regla también se desencadena cuando un método que es transparente o está marcado con <xref:System.Security.SecuritySafeCriticalAttribute> reemplaza un método marcado con un <xref:System.Security.SecurityCriticalAttribute> .

 Se aplica la regla al invalidar un método virtual o implementar una interfaz.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla se desencadena en los intentos de cambiar la accesibilidad de seguridad de un método más allá de la cadena de herencia. Por ejemplo, si un método virtual de una clase base es transparente o crítico para la seguridad, la clase derivada debe reemplazarlo con un método transparente o crítico para la seguridad. Por el contrario, si el virtual es crítico para la seguridad, la clase derivada debe reemplazarlo por un método crítico para la seguridad. La misma regla se aplica a la implementación de métodos de interfaz.

 Las reglas de transparencia se aplican cuando se compila el código JIT en lugar de hacerlo en tiempo de ejecución, de modo que el cálculo de transparencia no tiene información de tipo dinámico. Por consiguiente, el resultado del cálculo de transparencia debe poder determinarse únicamente a partir de los tipos estáticos que se van a compilar con JIT, independientemente del tipo dinámico.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie la transparencia del método que invalide un método virtual o implemente una interfaz para que coincida con la transparencia del método virtual o de la interfaz.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Las infracciones de esta regla darán lugar a un tiempo de ejecución <xref:System.TypeLoadException> para los ensamblados que usan la transparencia de nivel 2.

## <a name="examples"></a>Ejemplos

### <a name="code"></a>Código
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2134.methodsmustoverridewithconsistenttransparency/cs/ca2134 - methodsmustoverridewithconsistenttransparency.cs#1)]

## <a name="see-also"></a>Consulte también
 [Código transparente en seguridad, nivel 2](https://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)
