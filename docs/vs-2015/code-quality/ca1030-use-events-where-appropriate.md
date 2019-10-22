---
title: 'CA1030: usar eventos cuando sea apropiado | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7ab3a576b5014799e470260567a4942b5c3ef9de
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661921"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: Utilizar eventos cuando sea apropiado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|Identificador de comprobación|CA1030|
|Categoría|Microsoft. Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un nombre de método público, protegido o privado comienza con uno de los siguientes:

- Suplementa

- Cambio de movimiento

- Inflama

- Generar

## <a name="rule-description"></a>Descripción de la regla
 Esta regla detecta métodos que tienen nombres que normalmente se utilizarían para eventos. Los eventos siguen el modelo de diseño de observador o publicación-suscripción. se utilizan cuando un cambio de estado en un objeto debe comunicarse con otros objetos. Si se llama a un método en respuesta a un cambio de estado claramente definido, un controlador de eventos debe invocar el método. Los objetos que llaman al método deben provocar eventos en lugar de llamar directamente al método.

 Algunos ejemplos comunes de eventos se encuentran en las aplicaciones de la interfaz de usuario, en las que una acción del usuario, como hacer clic en un botón, hace que se ejecute un segmento de código. El modelo de eventos [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] no se limita a las interfaces de usuario; debe usarse en cualquier lugar en el que deba comunicar los cambios de estado a uno o varios objetos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Si se llama al método cuando cambia el estado de un objeto, considere la posibilidad de cambiar el diseño para usar el modelo de eventos [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla si el método no funciona con el modelo de eventos [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].
