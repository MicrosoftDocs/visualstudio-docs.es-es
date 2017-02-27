---
title: "CA1030: Utilizar eventos cuando sea apropiado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseEventsWhereAppropriate"
  - "CA1030"
helpviewer_keywords: 
  - "CA1030"
  - "UseEventsWhereAppropriate"
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1030: Utilizar eventos cuando sea apropiado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseEventsWhereAppropriate|  
|Identificador de comprobación|CA1030|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un nombre de método público, protegido o privado comienza con una de las siguientes palabras:  
  
-   AddOn  
  
-   RemoveOn  
  
-   Fire  
  
-   Raise  
  
## Descripción de la regla  
 Esta regla detecta métodos que tienen nombres que normalmente se utilizarían para eventos.  Los eventos siguen el patrón de diseño publicación\-suscripción u observador; se utilizan cuando se debe comunicar un cambio de estado a otros objetos.  Si se llama a un método en respuesta a un cambio de estado claramente definido, un controlador de eventos debe invocar al método.  Los objetos que llaman al método deben provocar eventos en lugar de llamar directamente al método.  
  
 Se pueden encontrar algunos de los ejemplos habituales de eventos en las aplicaciones de interfaz de usuario, donde una acción del usuario como hacer clic en un botón provoca la ejecución de un segmento de código.  El modelo de evento de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] no se limita a las interfaces de usuario; deben utilizarse donde deba comunicarse un cambio de estado de uno o más objetos.  
  
## Cómo corregir infracciones  
 Si se llama al método cuando el cambia estado de un objeto, debería tener en cuenta el cambio en el diseño para utilizar el modelo de evento de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## Cuándo suprimir advertencias  
 Suprima una advertencia de esta regla si el método no funciona con el modelo de evento de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].