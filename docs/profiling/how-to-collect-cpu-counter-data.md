---
title: Procedimiento para recopilar datos de contadores de CPU | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.cpucounters
helpviewer_keywords:
- profiling tools, using portable CPU counters
- performance tools, portable CPU counters
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c500316bd53ddce8bf731876e5963e6ef253bb27
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2020
ms.locfileid: "85330926"
---
# <a name="how-to-collect-cpu-counter-data"></a>Procedimiento Recopilar datos de contadores de CPU

Un contador de eventos de CPU se utiliza para recopilar datos de rendimiento específicos de hardware. En este artículo se muestra cómo recopilar datos de contador de eventos cuando se usa el método de generación de perfiles de instrumentación.

Se producen dos tipos de eventos de contador de CPU:

- Eventos portátiles: eventos de CPU que se pueden recopilar independientemente de una CPU concreta.

- Eventos de plataforma: eventos de CPU que están asociados a una CPU específica.

  Los eventos portátiles incluyen eventos generales, como instrucciones retiradas y ciclos no detenidos, eventos de búfer de la CPU, eventos de bifurcación y eventos de caché L2. El fabricante del procesador determina los contadores de eventos de plataforma disponibles.

  Las categorías de eventos pueden compartirse entre los contadores de eventos portátiles y de plataforma. Por ejemplo, las siguientes categorías de datos son con frecuencia comunes a ambos tipos:

- Eventos de memoria.

- Eventos de front-end.

- Eventos de bifurcación.

  Puede recopilar datos del contador de rendimiento de dos formas en el generador de perfiles:

- Recopilar datos de uno o más contadores al generar perfiles mediante la instrumentación.

- Especificar un evento de contador como el intervalo de muestreo al generar perfiles mediante el muestreo. Para obtener más información, vea [Cómo: Elegir eventos de muestreo](../profiling/how-to-choose-sampling-events.md).

## <a name="to-collect-cpu-performance-counter-data-when-you-profile-by-instrumentation"></a>Para recopilar datos del contador de rendimiento de CPU al generar perfiles mediante la instrumentación

1. En las **Páginas de propiedades** de la sesión de rendimiento, haga clic en **Contadores de CPU**.

2. Seleccione la casilla **Recopilar contadores de CPU**.

3. Expanda el árbol **Contadores de rendimiento disponibles** hasta que encuentre los eventos de ejemplo que se van a recopilar.

4. Para cada evento que se va a recopilar, seleccione el evento y, a continuación, haga clic en la flecha derecha para agregar el evento a la lista **Contadores seleccionados**.

    > [!NOTE]
    > **Contadores de rendimiento disponibles** está habilitado solo si selecciona la casilla **Recopilar contadores de CPU**.

## <a name="see-also"></a>Vea también

[Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)
[Propiedades de las sesiones de rendimiento](../profiling/performance-session-properties.md)
[Contadores de Windows y de CPU](../profiling/cpu-and-windows-counters.md)
[ Elegir eventos de muestreo](../profiling/how-to-choose-sampling-events.md)
