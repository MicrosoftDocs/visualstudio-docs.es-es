---
title: "CA2133: Los delegados deben enlazarse a métodos con una transparencia coherente | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d5e5d391fc11fbefbe1f3cef6ee1512ab02d6b00
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133: Los delegados deben enlazarse a métodos con una transparencia coherente
|||  
|-|-|  
|TypeName|DelegatesMustBindWithConsistentTransparency|  
|Identificador de comprobación|CA2133|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
> [!NOTE]
>  Esta advertencia solo se aplica a código que se está ejecutando CoreCLR (la versión de CLR que es específica de las aplicaciones Silverlight Web).  
  
## <a name="cause"></a>Motivo  
 Esta advertencia se desencadena en un método que enlaza un delegado que está marcado con el <xref:System.Security.SecurityCriticalAttribute> a un método que es transparente o que está marcado con el <xref:System.Security.SecuritySafeCriticalAttribute>. La advertencia también desencadena un método que enlaza un delegado que es transparente o crítico para la seguridad a un método crítico.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Tipos de delegado y los métodos que se enlazan deben tener una transparencia coherente. Los delegados de transparentes y crítico para la seguridad solo pueden enlazar a otros métodos transparentes o crítico para la seguridad. De igual forma, los delegados críticos solo pueden enlazar a los métodos críticos. Estas reglas de enlace aseguran que el único código que puede invocar un método a través de un delegado también pudiera haber invocado el mismo método directamente. Por ejemplo, las reglas de enlace impiden que el código transparente al llamar a código crítico directamente a través de un delegado transparente.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta advertencia, cambie la transparencia del delegado o del método que enlaza para que la transparencia de los dos son equivalentes.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
### <a name="code"></a>Código  
 [!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2133-delegates-must-bind-to-methods-with-consistent-transparency_1.cs)]