---
title: "CA2122: No exponer indirectamente m&#233;todos con peticiones de v&#237;nculos | Microsoft Docs"
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
  - "CA2122"
  - "DoNotIndirectlyExposeMethodsWithLinkDemands"
helpviewer_keywords: 
  - "CA2122"
  - "DoNotIndirectlyExposeMethodsWithLinkDemands"
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2122: No exponer indirectamente m&#233;todos con peticiones de v&#237;nculos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|  
|Identificador de comprobación|CA2122|  
|Categoría|Microsoft.Security|  
|Cambio problemático|No|  
  
## Motivo  
 Un miembro público o protegido tiene un [Link Demands](../Topic/Link%20Demands.md) y es llamado por un miembro que no realiza ninguna comprobación de seguridad.  
  
## Descripción de la regla  
 Una solicitud de vínculo sólo comprueba los permisos del llamador inmediato.  Si un miembro `X` no realiza ninguna solicitud de seguridad de sus llamadores y llama al código protegido mediante una solicitud de vínculo, un llamador sin el permiso necesario puede utilizar `X` para obtener acceso al miembro protegido.  
  
## Cómo corregir infracciones  
 Agregue una solicitud de seguridad [Datos y modelado](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md) o de vínculo al miembro de modo que no proporcione más acceso no seguro al miembro protegido por solicitud de vínculo.  
  
## Cuándo suprimir advertencias  
 Para suprimir de forma segura una advertencia de esta regla, debe asegurarse de que el código no conceda a sus llamadores acceso a las operaciones o recursos que se puedan usar de forma destructiva.  
  
## Ejemplo  
 Los ejemplos siguientes muestran una biblioteca que infringe la regla y una aplicación que muestra la debilidad de la biblioteca.  La biblioteca de ejemplos proporciona dos métodos que juntos infringen la regla.  Una solicitud de vínculo protege al método `EnvironmentSetting` de un acceso no restringido a las variables de entorno.  El método `DomainInformation` no realiza ninguna solicitud de seguridad de sus llamadores antes de llamar a `EnvironmentSetting`.  
  
 [!code-cs[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]  
  
## Ejemplo  
 La aplicación siguiente llama al miembro de biblioteca no seguro.  
  
 [!code-cs[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **Valor del miembro no seguro: seattle.corp.contoso.com**   
## Vea también  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Link Demands](../Topic/Link%20Demands.md)   
 [Datos y modelado](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)