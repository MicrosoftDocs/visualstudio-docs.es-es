---
title: 'CA2133: Los delegados deben enlazarse a métodos con una transparencia coherente | Microsoft Docs'
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
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 16e766979e71b36f816e1265ef5da520c16d85b4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909712"
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
>  Esta advertencia solo se aplica al código que se está ejecutando el CoreCLR (la versión de CLR que es específica de aplicaciones Web de Silverlight).

## <a name="cause"></a>Motivo
 Esta advertencia se desencadena en un método que enlaza un delegado que está marcado con el <xref:System.Security.SecurityCriticalAttribute> a un método que es transparente o está marcado con el <xref:System.Security.SecuritySafeCriticalAttribute>. La advertencia también desencadena un método que enlaza un delegado que es transparente o crítico para la seguridad a un método crítico.

## <a name="rule-description"></a>Descripción de la regla
 Tipos de delegado y los métodos que se enlazan deben tener una transparencia coherente. Los delegados de transparentes y crítico para la seguridad solo pueden enlazar a otros métodos transparentes o crítico para la seguridad. De forma similar, los delegados críticos solo pueden enlazar a métodos críticos. Estas reglas de enlace garantizan que el único código que puede invocar un método a través de un delegado también pudiera haber invocado el mismo método directamente. Por ejemplo, reglas de enlace evitar que el código transparente de la llamada a código crítico directamente a través de un delegado transparente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta advertencia, cambie la transparencia del delegado o del método que enlaza para que la transparencia de los dos son equivalentes.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2133.delegatesmustbindwithconsistenttransparency/cs/ca2133 - delegatesmustbindwithconsistenttransparency.cs#1)]



