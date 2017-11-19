---
title: 'CA1030: Utilizar eventos cuando sea necesario | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4c07aac3780abc10dd3995b21b5c9636607166f8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: Utilizar eventos cuando sea apropiado
|||  
|-|-|  
|TypeName|UseEventsWhereAppropriate|  
|Identificador de comprobación|CA1030|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Un nombre de método público, protegido o privado comienza con uno de los siguientes:  
  
-   Complemento  
  
-   RemoveOn  
  
-   Activar  
  
-   Generar  
  
## <a name="rule-description"></a>Descripción de la regla  
 Esta regla detecta métodos que tienen nombres que normalmente se utilizarían para eventos. Los eventos siguen el patrón de diseño publicación-suscripción u observador; se usan cuando un cambio de estado en un objeto se debe comunicar con otros objetos. Si se invoca un método en respuesta a un cambio de estado claramente definido, se debe llamar al método mediante un controlador de eventos. Los objetos que llaman al método deben provocar eventos en lugar de llamar directamente al método.  
  
 Algunos ejemplos comunes de eventos se encuentran en las aplicaciones de interfaz de usuario que hace que un segmento de código para ejecutar una acción del usuario como hacer clic en un botón. El [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] modelo de evento no se limita a las interfaces de usuario; se debe usar desde cualquier lugar debe comunicar el estado cambia a uno o varios objetos.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Si el método se llama cuando cambia el estado de un objeto, considere la posibilidad de cambiar el diseño que se va a usar el [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] modelo de evento.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Suprimir una advertencia de esta regla si el método no funciona con el [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] modelo de evento.