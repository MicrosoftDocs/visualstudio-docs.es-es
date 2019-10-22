---
title: 'CA2133: los delegados deben enlazarse a métodos con una transparencia coherente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 487047b7dd3096e65a6e287d79d91d3029f3dc5a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72608995"
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133: Los delegados deben enlazarse a métodos con una transparencia coherente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DelegatesMustBindWithConsistentTransparency|
|Identificador de comprobación|CA2133|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

> [!NOTE]
> Esta advertencia solo se aplica al código que ejecuta CoreCLR (la versión de CLR que es específica de las aplicaciones Web de Silverlight).

## <a name="cause"></a>Motivo
 Esta advertencia se desencadena en un método que enlaza un delegado marcado con el <xref:System.Security.SecurityCriticalAttribute> a un método que es transparente o que está marcado con el <xref:System.Security.SecuritySafeCriticalAttribute>. La advertencia también desencadena un método que enlaza un delegado que es transparente o crítico para la seguridad a un método crítico.

## <a name="rule-description"></a>Descripción de la regla
 Los tipos de delegado y los métodos a los que se enlazan deben tener una transparencia coherente. Los delegados transparentes y críticos para la seguridad solo pueden enlazarse a otros métodos transparentes o críticos para la seguridad. De forma similar, los delegados críticos solo se pueden enlazar a métodos críticos. Estas reglas de enlace garantizan que el único código que puede invocar un método a través de un delegado podría haber invocado también el mismo método directamente. Por ejemplo, las reglas de enlace impiden que el código transparente llame directamente a código crítico a través de un delegado transparente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta advertencia, cambie la transparencia del delegado o del método que enlaza, de modo que la transparencia de los dos sea equivalente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2133.delegatesmustbindwithconsistenttransparency/cs/ca2133 - delegatesmustbindwithconsistenttransparency.cs#1)]
