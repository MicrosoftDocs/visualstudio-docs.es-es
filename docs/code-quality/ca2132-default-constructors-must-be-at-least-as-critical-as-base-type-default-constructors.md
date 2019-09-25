---
title: 'CA2132: Los constructores predeterminados deben ser al menos tan críticos para la seguridad como los constructores predeterminados de tipo base'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c5ca98219444515d01baf670489120238cb8dda
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232338"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132: Los constructores predeterminados deben ser al menos tan críticos para la seguridad como los constructores predeterminados de tipo base

|||
|-|-|
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|
|Identificador de comprobación|CA2132|
|Categoría|Microsoft.Security|
|Cambio importante|Problemático|

> [!NOTE]
> Esta advertencia solo se aplica al código que ejecuta CoreCLR (la versión de CLR que es específica de las aplicaciones Web de Silverlight).

## <a name="cause"></a>Motivo

El atributo Transparency del constructor predeterminado de una clase derivada no es tan importante como la transparencia de la clase base.

## <a name="rule-description"></a>Descripción de la regla

Los tipos y miembros que tienen <xref:System.Security.SecurityCriticalAttribute> el no se pueden usar en el código de aplicación de Silverlight. El código de confianza puede utilizar solo tipos y miembros críticos para la seguridad en .NET Framework para la biblioteca de clases de Silverlight. Dado que una construcción pública o protegida en una clase derivada debe tener la misma transparencia, o mayor, que su clase base, una clase de una aplicación no puede derivar de una clase marcada como SecurityCritical.

Para el código de plataforma de CoreCLR, si un tipo base tiene un constructor predeterminado no transparente público o protegido, el tipo derivado debe obedecer las reglas de herencia del constructor predeterminado. El tipo derivado también debe tener un constructor predeterminado y ese constructor debe ser al menos un constructor predeterminado crítico del tipo base.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir la infracción, quite el tipo o no se derive del tipo no transparente de seguridad.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima las advertencias de esta regla. Las infracciones de esta regla por código de aplicación darán lugar a que el CoreCLR no pueda cargar <xref:System.TypeLoadException>el tipo con un.

### <a name="code"></a>Código

[!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors_1.cs)]