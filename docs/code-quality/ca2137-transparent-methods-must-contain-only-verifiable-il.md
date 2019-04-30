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
ms.openlocfilehash: f74b539d9382bf8b5f5fe319ff319cdf6f372340
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806963"
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137: Los métodos transparentes deben contener solo IL que se pueda comprobar

|||
|-|-|
|TypeName|TransparentMethodsMustBeVerifiable|
|Identificador de comprobación|CA2137|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método contiene código que no se puede comprobar o devuelve un tipo por referencia.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla se desencadena en los intentos del código transparente en seguridad de ejecutar MSIL no comprobable (Lenguaje intermedio de Microsoft). Sin embargo, la regla no contiene un comprobador de IL completo y, en su lugar, utiliza la heurística para detectar la mayoría de las infracciones de comprobación MSIL.

 Para estar seguro de que el código solo contiene MSIL comprobable, ejecute [Peverify.exe (herramienta PEVerify)](/dotnet/framework/tools/peverify-exe-peverify-tool) en el ensamblado. Ejecutar PEVerify con la **/ transparente** opción que limita la salida a sólo puede comprobar los métodos transparentes que provocaría un error. Si la / opción transparente no se utiliza, PEVerify también comprueba los métodos críticos que pueden contener código no comprobable.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, marque el método con el <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> de atributo o quite el código no comprobable.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El método en este ejemplo usa código no comprobable y se debe marcar con el <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> atributo.

 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../code-quality/codesnippet/CSharp/ca2137-transparent-methods-must-contain-only-verifiable-il_1.cs)]