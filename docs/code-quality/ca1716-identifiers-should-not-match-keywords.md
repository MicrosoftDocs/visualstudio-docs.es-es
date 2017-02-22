---
title: "CA1716: Los identificadores no deber&#237;an coincidir con palabras clave | Microsoft Docs"
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
  - "IdentifiersShouldNotMatchKeywords"
  - "CA1716"
helpviewer_keywords: 
  - "IdentifiersShouldNotMatchKeywords"
  - "CA1716"
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1716: Los identificadores no deber&#237;an coincidir con palabras clave
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotMatchKeywords|  
|Identificador de comprobación|CA1716|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un nombre de un espacio de nombres, de un tipo, o de un miembro virtual o de interfaz coincide con una palabra clave reservada en un lenguaje de programación.  
  
## Descripción de la regla  
 Los identificadores de espacios de nombres, tipos y miembros virtuales o de interfaz no deben coincidir con palabras clave definidas por los lenguajes que tienen como destino Common Language Runtime.  Dependiendo del lenguaje que se use y de la palabra clave, los errores del compilador y las ambigüedades pueden hacer que sea complicado utilizar la biblioteca.  
  
 Esta regla comprueba las palabras clave en los lenguajes siguientes:  
  
-   Visual Basic  
  
-   C\#  
  
-   C\+\+\/CLI  
  
 La comparación sin distinción entre mayúsculas y minúsculas se utiliza para las palabras clave de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] y la comparación con distinción entre mayúsculas y minúsculas se utiliza para los otros lenguajes.  
  
## Cómo corregir infracciones  
 Seleccione un nombre que no aparece en la lista de palabras clave.  
  
## Cuándo suprimir advertencias  
 Puede suprimir una advertencia de esta regla si está convencido d que el identificador no confundirá a los usuarios de la API, y que la biblioteca es utilizable en todos los lenguajes disponibles en [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].