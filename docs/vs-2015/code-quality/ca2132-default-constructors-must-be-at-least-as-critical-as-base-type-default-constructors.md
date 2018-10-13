---
title: 'CA2132: Los constructores predeterminados deben ser al menos tan críticos como los constructores predeterminados de tipo base | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3237b9350492ed5e7cd323b38cd4dae4b30a5db9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49243248"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132: Los constructores predeterminados deben ser al menos tan críticos para la seguridad como los constructores predeterminados de tipo base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|
|Identificador de comprobación|CA2132|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

> [!NOTE]
>  Esta advertencia solo se aplica al código que se está ejecutando el CoreCLR (la versión de CLR que es específica de aplicaciones Web de Silverlight).

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
 [!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2132.defaultconstructorsmusthaveconsistenttransparency/cs/ca2132 - defaultconstructorsmusthaveconsistenttransparency.cs#1)]

### <a name="comments"></a>Comentarios



