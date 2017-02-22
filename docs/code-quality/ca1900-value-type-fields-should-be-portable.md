---
title: "CA1900: Los campos de tipos de valor deber&#237;an ser port&#225;tiles | Microsoft Docs"
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
  - "CA1900"
  - "ValueTypeFieldsShouldBePortable"
helpviewer_keywords: 
  - "ValueTypeFieldsShouldBePortable"
  - "CA1900"
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1900: Los campos de tipos de valor deber&#237;an ser port&#225;tiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ValueTypeFieldsShouldBePortable|  
|Identificador de comprobación|CA1900|  
|Categoría|Microsoft.Portability|  
|Cambio problemático|Problemático: si el campo se puede ver fuera del ensamblado.<br /><br /> No problemático: si el campo no es visible fuera del ensamblado.|  
  
## Motivo  
 Esta regla comprueba que las estructuras declaradas con un diseño explícito se alinearán correctamente cuando se calculen las referencias al código no administrado en sistemas operativos de 64 bits.  IA\-64 no permite accesos a memoria no alineada y el proceso se bloqueará si no se corrige esta infracción.  
  
## Descripción de la regla  
 Las estructuras que tienen un diseño explícito que contiene campos no alineados producen bloqueos en los sistemas operativos de 64 bits.  
  
## Cómo corregir infracciones  
 Todos los campos que tengan menos de 8 bytes deben tener posiciones de desplazamiento que sean múltiplo de su tamaño, y los campos de 8 bytes o más deben tener posiciones de desplazamiento que sean múltiplo de 8.  Otra solución es utilizar `LayoutKind.Sequential` en lugar de `LayoutKind.Explicit`, si es razonable.  
  
## Cuándo suprimir advertencias  
 Únicamente se debe suprimir esta advertencia si se produce por un error.