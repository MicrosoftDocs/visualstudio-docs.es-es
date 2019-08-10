---
title: 'CA2137: Los métodos transparentes deben contener solo IL que se pueda comprobar'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98b75a9f67a24fd8bea1ecc3a8782b6bd9e6b34b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920607"
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137: Los métodos transparentes deben contener solo IL que se pueda comprobar

|||
|-|-|
|TypeName|TransparentMethodsMustBeVerifiable|
|Identificador de comprobación|CA2137|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Un método contiene código que no se puede comprobar o devuelve un tipo por referencia.

## <a name="rule-description"></a>Descripción de la regla
Esta regla se desencadena en los intentos del código transparente en seguridad de ejecutar MSIL no comprobable (Lenguaje intermedio de Microsoft). Sin embargo, la regla no contiene un comprobador de IL completo y, en su lugar, utiliza la heurística para detectar la mayoría de las infracciones de comprobación MSIL.

Para asegurarse de que el código solo contiene MSIL comprobable, ejecute [peverify. exe (herramienta peverify)](/dotnet/framework/tools/peverify-exe-peverify-tool) en el ensamblado. Ejecute PEVerify con la opción **/transparent** , que limita la salida a solo los métodos transparentes no comprobables, lo que produciría un error. Si no se usa la opción/Transparent, PEVerify también comprueba los métodos críticos que pueden contener código no comprobable.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, marque el método con <xref:System.Security.SecurityCriticalAttribute> el <xref:System.Security.SecuritySafeCriticalAttribute> atributo o o quite el código no comprobable.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
El método en este ejemplo utiliza código no comprobable y debe marcarse con el <xref:System.Security.SecurityCriticalAttribute> atributo <xref:System.Security.SecuritySafeCriticalAttribute> o.

[!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../code-quality/codesnippet/CSharp/ca2137-transparent-methods-must-contain-only-verifiable-il_1.cs)]