---
title: "CA2108: Revisar la seguridad declarativa en los tipos de valor | Microsoft Docs"
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
  - "ReviewDeclarativeSecurityOnValueTypes"
  - "CA2108"
helpviewer_keywords: 
  - "CA2108"
  - "ReviewDeclarativeSecurityOnValueTypes"
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2108: Revisar la seguridad declarativa en los tipos de valor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewDeclarativeSecurityOnValueTypes|  
|Identificador de comprobación|CA2108|  
|Categoría|Microsoft.Security|  
|Cambio problemático|No|  
  
## Motivo  
 Un [Datos y modelado](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md) o [Link Demands](../Topic/Link%20Demands.md) protege un tipo de valor público o protegido.  
  
## Descripción de la regla  
 Antes de que otros constructores se ejecuten, los constructores predeterminados asignan e inicializan los tipos de valor.  Si Demand o LinkDemand protegen un tipo de valor y el llamador no tiene permisos para cumplir la comprobación de seguridad, cualquier constructor que no sea el predeterminado producirá un error y se producirá una excepción de seguridad.  No se desasigna el tipo de valor; permanece en el estado establecido por su constructor predeterminado.  No suponga que un llamador que pasa una instancia del tipo de valor tiene permiso para crear o tener acceso a la instancia.  
  
## Cómo corregir infracciones  
 No puede corregir una infracción de esta regla a menos que quite la comprobación de seguridad del tipo y en su lugar utilice las comprobaciones de seguridad de nivel de método.  Observe que al corregir la infracción de esta manera, no se evitará que los llamadores con permisos inadecuados obtengan instancias del tipo de valor.  Debe asegurarse de que una instancia del tipo de valor, en su estado predeterminado, no exponga información confidencial y no se pueda utilizar de forma peligrosa.  
  
## Cuándo suprimir advertencias  
 Puede suprimir una advertencia de esta regla si un llamador puede obtener instancias del tipo de valor en su estado predeterminado sin representar ninguna amenaza para la seguridad.  
  
## Ejemplo  
 El ejemplo siguiente muestra una biblioteca que contiene un tipo de valor que infringe esta regla.  Tenga en cuenta que el tipo `StructureManager` supone que un llamador que pasa una instancia del tipo de valor tiene permiso para crear o tener acceso a la instancia.  
  
 [!code-cs[FxCop.Security.DemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_1.cs)]  
  
## Ejemplo  
 La aplicación siguiente muestra la debilidad de la biblioteca.  
  
 [!code-cs[FxCop.Security.TestDemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_2.cs)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **Constructor de estructuras personalizado: error de solicitud.**  
**Nuevos valores SecuredTypeStructure 100 100**  
**Nuevos valores SecuredTypeStructure 200 200**   
## Vea también  
 [Link Demands](../Topic/Link%20Demands.md)   
 [Datos y modelado](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)