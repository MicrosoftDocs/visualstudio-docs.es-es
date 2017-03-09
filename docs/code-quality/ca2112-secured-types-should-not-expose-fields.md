---
title: "CA2112: Los tipos seguros no deber&#237;an exponer campos | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2112"
  - "SecuredTypesShouldNotExposeFields"
helpviewer_keywords: 
  - "CA2112"
  - "SecuredTypesShouldNotExposeFields"
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2112: Los tipos seguros no deber&#237;an exponer campos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SecuredTypesShouldNotExposeFields|  
|Identificador de comprobación|CA2112|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo público o protegido contiene los campos públicos y está protegido por [Link Demands](../Topic/Link%20Demands.md).  
  
## Descripción de la regla  
 Si el código tiene acceso a una instancia de tipo que está protegida por una solicitud de vínculo, el código no cumplirá la solicitud para obtener acceso a los campos del tipo.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, especifique los campos como no públicos y agregue propiedades o métodos públicos que devuelven los datos de campo.  Las comprobaciones de seguridad de LinkDemand de los tipos protegen el acceso a las propiedades y métodos del tipo.  Sin embargo, la seguridad de acceso del código no se aplica a los campos.  
  
## Cuándo suprimir advertencias  
 Tanto para evitar problemas de seguridad como para conseguir un diseño óptimo, debe corregir las infracciones estableciendo los campos públicos como no públicos.  Puede suprimir una advertencia de esta regla si los campos no contienen información que deba permanecer segura y si no confía en el contenido del campo.  
  
## Ejemplo  
 El siguiente ejemplo está compuesto por un tipo de biblioteca \(`SecuredTypeWithFields`\) con campos no seguros, un tipo \(`Distributor`\) que crea instancias del tipo de la biblioteca y pasa erróneamente instancias a tipos que no tienen permiso para crearlas, y código de aplicación que puede leer los campos de la instancia a pesar de que no tiene el permiso que protege al tipo.  
  
 El código de la biblioteca siguiente infringe la regla.  
  
 [!code-cs[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]  
  
## Ejemplo  
 La aplicación no puede crear una instancia debido a la solicitud de vínculo que protege el tipo.  La clase siguiente permite que la aplicación obtenga una instancia del tipo protegido.  
  
 [!code-cs[FxCop.Security.LDOnFieldsDistributor#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]  
  
## Ejemplo  
 La aplicación siguiente muestra cómo obtiene acceso el código a los campos sin el permiso para tener acceso a los métodos de un tipo protegido.  
  
 [!code-cs[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_3.cs)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **Crear una instancia de SecuredTypeWithFields.**  
**Campos de tipo protegido: 22, 33**  
**Cambiando el campo de tipo seguro...**  
**Campos de objeto almacenado en caché: 99, 33**   
## Reglas relacionadas  
 [CA1051: No declarar campos de instancia visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## Vea también  
 [Link Demands](../Topic/Link%20Demands.md)   
 [Datos y modelado](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)