---
title: 'CA1030: Utilizar eventos cuando sea apropiado | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: 8100aff6c2215d9a5fa031d69fc0ee105e440e3a
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47592237"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: Utilizar eventos cuando sea apropiado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA1030: utilizar eventos cuando sea apropiado](https://docs.microsoft.com/visualstudio/code-quality/ca1030-use-events-where-appropriate).

|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|Identificador de comprobación|CA1030|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Nombre de un método público, protegido o privado comienza con uno de los siguientes:

-   AddOn

-   RemoveOn

-   Fuego

-   Raise

## <a name="rule-description"></a>Descripción de la regla
 Esta regla detecta métodos que tienen nombres que normalmente se utilizarían para eventos. Los eventos siguen el patrón de diseño publicación-suscripción u observador; se utilizan cuando un cambio de estado en un objeto debe comunicarse con otros objetos. Si se llama un método en respuesta a un cambio de estado claramente definido, se debe llamar al método mediante un controlador de eventos. Los objetos que llaman al método deben provocar eventos en lugar de llamar directamente al método.

 Algunos ejemplos comunes de los eventos se encuentran en las aplicaciones de interfaz de usuario que hace que un segmento de código para ejecutar una acción del usuario como hacer clic en un botón. El [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] modelo de evento no se limita a las interfaces de usuario; se debe usar en cualquier lugar que debe comunicar el estado cambia a uno o más objetos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Si el método se llama cuando cambia el estado de un objeto, considere la posibilidad de cambiar el diseño para utilizar el [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] modelo de evento.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla si el método no funciona con el [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] modelo de evento.



