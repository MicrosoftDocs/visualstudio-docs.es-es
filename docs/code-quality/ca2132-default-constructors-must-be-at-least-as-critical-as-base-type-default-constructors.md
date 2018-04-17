---
title: 'CA2132: Los constructores predeterminados deben ser al menos tan críticos como constructores predeterminados del tipo base | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed3e86eee97bff0afed761234c3d2fbe41dc1d1b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132: Los constructores predeterminados deben ser al menos tan críticos para la seguridad como los constructores predeterminados de tipo base
|||  
|-|-|  
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|  
|Identificador de comprobación|CA2132|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
> [!NOTE]
>  Esta advertencia solo se aplica a código que se está ejecutando CoreCLR (la versión de CLR que es específica de las aplicaciones Silverlight Web).  
  
## <a name="cause"></a>Motivo  
 El atributo de transparencia del constructor predeterminado de una clase derivada no es tan crítico como la transparencia de la clase base.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Tipos y miembros que tienen el <xref:System.Security.SecurityCriticalAttribute> no se puede usar el código de aplicación de Silverlight. El código de confianza puede utilizar solo tipos y miembros críticos para la seguridad en .NET Framework para la biblioteca de clases de Silverlight. Dado que una construcción pública o protegida en una clase derivada debe tener la misma transparencia, o mayor, que su clase base, una clase de una aplicación no puede derivar de una clase marcada como SecurityCritical.  
  
 Para el código de plataforma de CoreCLR, si un tipo base tiene un constructor predeterminado no transparente público o protegido, a continuación, el tipo derivado debe obedecer las reglas de herencia del constructor predeterminado. El tipo derivado también debe tener un constructor predeterminado y este constructor debe ser al menos como constructor predeterminado crítico del tipo base.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir la infracción, quite el tipo o no se derivan de tipo no es transparente en seguridad.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla. Las infracciones de esta regla por código de aplicación dará como resultado CoreCLR rechace cargar el tipo con un <xref:System.TypeLoadException>.  
  
### <a name="code"></a>Código  
 [!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors_1.cs)]  
  
### <a name="comments"></a>Comentarios