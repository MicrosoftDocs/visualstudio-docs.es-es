---
title: "CA1020: Evitar espacios de nombres con pocos tipos | Microsoft Docs"
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
  - "CA1020"
  - "AvoidNamespacesWithFewTypes"
helpviewer_keywords: 
  - "AvoidNamespacesWithFewTypes"
  - "CA1020"
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1020: Evitar espacios de nombres con pocos tipos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidNamespacesWithFewTypes|  
|Identificador de comprobación|CA1020|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un espacio de nombres distinto del espacio de nombres global contiene menos de cinco tipos.  
  
## Descripción de la regla  
 Asegúrese de que cada espacio de nombres tiene una organización lógica, y que hay una razón válida para colocar tipos en un espacio de nombres apenas lleno.  Los espacios de nombres deben contener tipos que se utilizan juntos en la mayoría de los escenarios.  Cuando las aplicaciones son mutuamente exclusivas, los tipos se deben buscar en espacios de nombres independientes.  Por ejemplo, el espacio de nombres <xref:System.Web.UI> contiene tipos que se utilizan en las aplicaciones web, y el espacio de nombres <xref:System.Windows.Forms> contiene tipos que se utilizan en aplicaciones basadas en [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)].  Aunque ambos espacios de nombres tienen tipos que controlan aspectos de la interfaz de usuario, estos tipos no están diseñados para su uso en la misma aplicación.  Por ello, se encuentran en espacios de nombres separados.  La organización de espacio de nombres especial también puede ser útil puesto que aumenta la capacidad de detectar una característica.  Examinando la jerarquía de espacio de nombres, los usuarios de la biblioteca deben poder buscar los tipos que implementan una característica.  
  
> [!NOTE]
>  Los tipos y permisos en tiempo de diseño no se deben combinar dentro de los otros espacios de nombres para cumplir esta regla.  Estos tipos pertenecen a sus propios espacios de nombres debajo de su espacio de nombres principal, y los espacios de nombres deben terminar con `.Design` y `.Permissions`, respectivamente.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, intente combinar los espacios de nombres que solo contienen unos pocos tipos dentro de un espacio de nombres único.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla cuando el espacio de nombres no contenga tipos que se usen con tipos en otros espacios de nombres.