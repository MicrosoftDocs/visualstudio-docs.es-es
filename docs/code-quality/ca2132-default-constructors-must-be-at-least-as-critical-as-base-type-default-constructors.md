---
title: "CA2132: Los constructores predeterminados deben ser al menos tan cr&#237;ticos para la seguridad como los constructores predeterminados de tipo base | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2132"
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2132: Los constructores predeterminados deben ser al menos tan cr&#237;ticos para la seguridad como los constructores predeterminados de tipo base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|  
|Identificador de comprobación|CA2132|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
> [!NOTE]
>  Esta advertencia solo se aplica al código que está ejecutando CoreCLR \(la versión de CLR que es específica de las aplicaciones web de Silverlight\).  
  
## Motivo  
 El atributo de transparencia del constructor predeterminado de una clase derivada no es tan crítico como la transparencia de la clase base.  
  
## Descripción de la regla  
 El código de aplicación de Silverlight no puede utilizar tipos y miembros que tengan <xref:System.Security.SecurityCriticalAttribute>.  El código de confianza puede utilizar solo tipos y miembros críticos para la seguridad en .NET Framework para la biblioteca de clases de Silverlight.  Dado que una construcción pública o protegida en una clase derivada debe tener la misma transparencia, o mayor, que su clase base, una clase de una aplicación no puede derivar de una clase marcada como SecurityCritical.  
  
 Para el código de plataforma de CoreCLR, si un tipo base tiene un constructor predeterminado no transparente público o protegido, el tipo derivado debe obedecer las reglas de herencia del constructor predeterminado.  El tipo derivado también debe tener un constructor predeterminado y ese constructor debe ser al menos tan crítico como el constructor predeterminado del tipo base.  
  
## Cómo corregir infracciones  
 Para corregir la infracción, quite el tipo o no realice derivaciones de un tipo con seguridad no transparente.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  Las infracciones de esta regla por código de aplicación harán que CoreCLR rechace cargar el tipo con una <xref:System.TypeLoadException>.  
  
### Código  
 [!code-cs[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors_1.cs)]  
  
### Comentarios