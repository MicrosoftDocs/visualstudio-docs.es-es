---
title: "CA2123: Las peticiones de v&#237;nculos de reemplazo deber&#237;an ser id&#233;nticas a la base | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2123"
  - "OverrideLinkDemandsShouldBeIdenticalToBase"
helpviewer_keywords: 
  - "CA2123"
  - "OverrideLinkDemandsShouldBeIdenticalToBase"
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2123: Las peticiones de v&#237;nculos de reemplazo deber&#237;an ser id&#233;nticas a la base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|  
|Identificador de comprobación|CA2123|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un método público o protegido de un tipo público reemplaza a un método o implementa una interfaz, y no tiene la misma [Link Demands](../Topic/Link%20Demands.md) que la interfaz y el método virtual.  
  
## Descripción de la regla  
 Esta regla compara un método con su método base, que es una interfaz o un método virtual de otro tipo y, a continuación, compara las solicitudes de vínculos en cada uno.  Se crea un informe de infracción si el método o el método base tiene una petición de vínculo y el otro no.  
  
 Si se infringe esta regla, un llamador malintencionado puede omitir la solicitud de vínculo simplemente llamando al método no seguro.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, aplique la misma solicitud de vínculo al método de reemplazo o a la implementación.  Si no es posible, marque el método con una demanda completa o quita el atributo.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El ejemplo siguiente muestra distintas infracciones de esta regla.  
  
 [!code-cs[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]  
  
## Vea también  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Link Demands](../Topic/Link%20Demands.md)