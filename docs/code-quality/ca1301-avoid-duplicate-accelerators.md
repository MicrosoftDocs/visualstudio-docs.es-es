---
title: "CA1301: Evitar aceleradores duplicados | Microsoft Docs"
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
  - "CA1301"
  - "AvoidDuplicateAccelerators"
helpviewer_keywords: 
  - "CA1301"
  - "AvoidDuplicateAccelerators"
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1301: Evitar aceleradores duplicados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidDuplicateAccelerators|  
|Identificador de comprobación|CA1301|  
|Categoría|Microsoft.Globalization|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un tipo extiende <xref:System.Windows.Forms.Control?displayProperty=fullName> y contiene dos o más controles de nivel superior que tienen teclas de acceso idénticas que se almacenan en un archivo de recursos.  
  
## Descripción de la regla  
 Una tecla de acceso, también denominada acelerador, permite el acceso mediante teclado a un control utilizando la tecla ALT.  Cuando varios controles tienen teclas de acceso duplicadas, no se define correctamente el comportamiento de la tecla de acceso.  Puede ocurrir que el usuario no tenga acceso al control deseado utilizando la tecla de acceso y que se habilite un control distinto al que desea.  
  
 La implementación actual de esta regla omite los elementos de menú.  Sin embargo, los elementos de menú en el mismo submenú no deberían tener teclas de acceso idénticas.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, defina teclas de acceso únicas para todos los controles.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El ejemplo siguiente muestra un formulario mínimo que contiene dos controles con teclas de acceso idénticas.  Las teclas se almacenan en un archivo de recursos, que no se muestra; sin embargo, sus valores aparecen en las líneas con comentario `checkBox.Text`.  El comportamiento de aceleradores duplicados puede examinarse intercambiando las líneas `checkBox.Text` con sus homólogas con comentarios.  Sin embargo, en este caso, el ejemplo no generará una advertencia de la regla.  
  
 [!code-cs[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]  
  
## Vea también  
 <xref:System.Resources.ResourceManager?displayProperty=fullName>   
 [Recursos de aplicaciones de escritorio](../Topic/Resources%20in%20Desktop%20Apps.md)