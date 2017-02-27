---
title: "CA2133: Los delegados deben enlazarse a m&#233;todos con una transparencia coherente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2133"
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA2133: Los delegados deben enlazarse a m&#233;todos con una transparencia coherente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DelegatesMustBindWithConsistentTransparency|  
|Identificador de comprobación|CA2133|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
> [!NOTE]
>  Esta advertencia solo se aplica al código que está ejecutando CoreCLR \(la versión de CLR que es específica de las aplicaciones web de Silverlight\).  
  
## Motivo  
 Esta advertencia se desencadena en un método que enlaza un delegado que está marcado con <xref:System.Security.SecurityCriticalAttribute> a un método que es transparente o que está marcado con <xref:System.Security.SecuritySafeCriticalAttribute>.  La advertencia también desencadena un método que enlaza un delegado que es transparente o crítico para la seguridad a un método crítico.  
  
## Descripción de la regla  
 Los tipos delegados y los métodos a los que están enlazados deben tener una transparencia coherente.  Los delegados transparentes y críticos para la seguridad y disponible desde código transparente solo pueden enlazarse a métodos transparentes o críticos para la seguridad y disponible desde código transparente.  De forma similar, los delegados críticos para la seguridad solo pueden enlazarse a métodos críticos para la seguridad.  Estas reglas de enlace aseguran que el único código que puede invocar un método a través de un delegado también pudiera haber invocado directamente el mismo método.  Por ejemplo, las reglas de enlace evitan que el código transparente llame directamente al código crítico a través de un delegado transparente.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta advertencia, cambie la transparencia del delegado o del método al que enlaza para que la transparencia de los dos sea equivalente.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
### Código  
 [!code-cs[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2133-delegates-must-bind-to-methods-with-consistent-transparency_1.cs)]