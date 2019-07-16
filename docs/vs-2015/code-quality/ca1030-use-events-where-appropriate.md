---
title: 'CA1030: Utilizar eventos cuando sea apropiado | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9d00db6f9a00a273198cc50704d65ed6d2e4bb33
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157698"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: Utilizar eventos cuando sea apropiado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|Identificador de comprobación|CA1030|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Nombre de un método público, protegido o privado comienza con uno de los siguientes:

- AddOn

- RemoveOn

- Fuego

- Raise

## <a name="rule-description"></a>Descripción de la regla
 Esta regla detecta métodos que tienen nombres que normalmente se utilizarían para eventos. Los eventos siguen el patrón de diseño publicación-suscripción u observador; se utilizan cuando un cambio de estado en un objeto debe comunicarse con otros objetos. Si se llama un método en respuesta a un cambio de estado claramente definido, se debe llamar al método mediante un controlador de eventos. Los objetos que llaman al método deben provocar eventos en lugar de llamar directamente al método.

 Algunos ejemplos comunes de los eventos se encuentran en las aplicaciones de interfaz de usuario que hace que un segmento de código para ejecutar una acción del usuario como hacer clic en un botón. El [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] modelo de evento no se limita a las interfaces de usuario; se debe usar en cualquier lugar que debe comunicar el estado cambia a uno o más objetos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Si el método se llama cuando cambia el estado de un objeto, considere la posibilidad de cambiar el diseño para utilizar el [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] modelo de evento.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla si el método no funciona con el [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] modelo de evento.
