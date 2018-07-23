---
title: 'CA2132: Los constructores predeterminados deben ser al menos tan críticos para la seguridad como los constructores predeterminados de tipo base'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9602ccd4aae7f3df1a708728203e2ad1c0857776
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176855"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132: Los constructores predeterminados deben ser al menos tan críticos para la seguridad como los constructores predeterminados de tipo base

|||
|-|-|
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|
|Identificador de comprobación|CA2132|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

> [!NOTE]
> Esta advertencia solo se aplica al código que se está ejecutando el CoreCLR (la versión de CLR que es específica para las aplicaciones web de Silverlight).

## <a name="cause"></a>Motivo

El atributo de transparencia del constructor predeterminado de una clase derivada no es tan crítico como la transparencia de la clase base.

## <a name="rule-description"></a>Descripción de la regla

Tipos y miembros que tienen el <xref:System.Security.SecurityCriticalAttribute> no se puede usar código de aplicación de Silverlight. El código de confianza puede utilizar solo tipos y miembros críticos para la seguridad en .NET Framework para la biblioteca de clases de Silverlight. Dado que una construcción pública o protegida en una clase derivada debe tener la misma transparencia, o mayor, que su clase base, una clase de una aplicación no puede derivar de una clase marcada como SecurityCritical.

Para el código de plataforma de CoreCLR, si un tipo base tiene un constructor predeterminado no transparente público o protegido, a continuación, el tipo derivado debe obedecer las reglas de herencia del constructor predeterminado. El tipo derivado también debe tener un constructor predeterminado y ese constructor debe ser al menos de su constructor predeterminado crítica del tipo base.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir la infracción, quite el tipo o no se derivan de tipo que no sean transparentes en seguridad.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima las advertencias de esta regla. Las infracciones de esta regla de código de aplicación dará como resultado el CoreCLR rehúsa a cargar el tipo con un <xref:System.TypeLoadException>.

### <a name="code"></a>Código

[!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors_1.cs)]