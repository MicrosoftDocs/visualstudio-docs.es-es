---
title: 'CA1030: Utilizar eventos cuando sea apropiado'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 28d71fbfc10532f7c9420ea7e847ef4c29b88854
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236075"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: Utilizar eventos cuando sea apropiado

|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|Identificador de comprobación|CA1030|
|Categoría|Microsoft.Design|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Un nombre de método comienza con uno de los siguientes:

- AddOn
- Cambio de movimiento
- Inflama
- generar

De forma predeterminada, esta regla solo examina los métodos visibles externamente, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Esta regla detecta métodos que tienen nombres que normalmente se utilizarían para eventos. Los eventos siguen el modelo de diseño de observador o publicación-suscripción. se utilizan cuando un cambio de estado en un objeto debe comunicarse con otros objetos. Si se llama a un método en respuesta a un cambio de estado claramente definido, un controlador de eventos debe invocar el método. Los objetos que llaman al método deben provocar eventos en lugar de llamar directamente al método.

Algunos ejemplos comunes de eventos se encuentran en las aplicaciones de la interfaz de usuario, en las que una acción del usuario, como hacer clic en un botón, hace que se ejecute un segmento de código. El modelo de eventos de .NET no se limita a las interfaces de usuario. Debe usarse en cualquier lugar en el que deba comunicar los cambios de estado a uno o varios objetos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Si se llama al método cuando cambia el estado de un objeto, considere la posibilidad de cambiar el diseño para usar el modelo de eventos de .NET.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Suprima una advertencia de esta regla si el método no funciona con el modelo de eventos de .NET.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1030.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (diseño). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).
