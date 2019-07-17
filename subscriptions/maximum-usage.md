---
title: Uso de la característica Uso máximo en el portal de administración
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/24/2019
ms.topic: conceptual
description: Más información sobre cómo consultar el número máximo de suscripciones asignadas en el portal de administración
ms.openlocfilehash: 0442671a6cdb24e394e6c2a47c935ae894cca354
ms.sourcegitcommit: f369ff7e84b0216f01570a486c7be80ca6d0e61a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68250746"
---
# <a name="using-the-maximum-usage-feature-to-track-the-number-of-assigned-subscriptions"></a>Uso de la característica Uso máximo para realizar un seguimiento del número de suscripciones asignadas

Esta nueva característica del portal de administración de suscripciones de Visual Studio permite realizar un seguimiento de cuántas suscripciones ha comprado y asignado, así como identificar el número máximo de suscripciones de cada nivel que haya asignado, tanto durante el último año como a lo largo de la duración de sus contratos. 

## <a name="viewing-maximum-usage"></a>Visualización del uso máximo

Para consultar el número máximo de suscripciones asignadas a cualquier contrato y nivel de suscripción:

1. Seleccione el contrato que quiera consultar en la lista desplegable de la parte superior izquierda del portal. (Si solo tiene un contrato, ya estará seleccionado).

2. Haga clic en la pestaña **Uso máximo**.  
    > [!div class="mx-imgBorder"]
    > ![Menú Uso máximo](_img/maximum-usage/maximum-usage-menu.png)

3. Aparecerá la sección "Resumen de uso máximo", en la que se mostrará el número máximo de suscripciones que ha asignado durante el año pasado a cada nivel, junto con la fecha en la que alcanzó dicho máximo.  Si ha llegado más de una vez a dicho máximo, se mostrará la primera vez que lo alcanzó. 
    > [!div class="mx-imgBorder"]
    > ![Resumen de uso máximo](_img/maximum-usage/maximum-usage-summary.png)

4. Para ver el número máximo de suscripciones asignadas a toda la duración del contrato, haga clic en la pestaña **Full-Term** (Período completo).

## <a name="viewing-assignment-history"></a>Visualización del historial de asignaciones

Además de consultar el número máximo de asignaciones para cada nivel de suscripción, puede ver una cuenta en ejecución de la actividad del contrato, incluidas las adquisiciones y asignaciones, haciendo clic en el botón **Export full report** (Exportar el informe completo).  

> [!div class="mx-imgBorder"]
> ![Informe completo de uso máximo](_img/maximum-usage/maximum-usage-full-report.png)

Para cada nivel de suscripción, el informe muestra la fecha en la que se alcanza un nuevo nivel máximo de asignaciones y el número de suscripciones que hayan comprado a partir de esa fecha, lo que permite consultar fácilmente las fechas en las que hubo sobreasignaciones.  

Por ejemplo, en la tabla anterior, puede ver que el día 13/12/2018 había 123 suscripciones de Visual Studio Enterprise en el contrato y que se asignaron 120.  El 8/1/2019, se asignó una suscripción más, con lo que el total ascendió a 121.  El día siguiente, se asignaron otras seis suscripciones y se agregaron otras cuatro al contrato para cubrir las nuevas asignaciones.  

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes
### <a name="q-how-is-the-information-in-the-maximum-usage-different-from-the-assignment-information-available-in-the-overview-section-on-the-left-side-of-the-portal"></a>P: ¿En qué se diferencia la información de Uso máximo de la información disponible en la sección "Introducción" a la izquierda del portal?

R:  En la información general se muestran las asignaciones actuales y las suscripciones disponibles para cada nivel de suscripción.  Puede ser muy diferente del número máximo de suscripciones asignadas al contrato en cualquier momento.  La característica Uso máximo permite ver cuándo se alcanzaron los niveles de asignación máximos y cuáles eran dichos niveles.  Se trata de una distinción importante, puesto que la facturación de suscripciones correspondiente al recuento ajustado se basa en el número máximo de suscripciones asignadas en cualquier momento. 

## <a name="next-steps"></a>Pasos siguientes
Si tiene alguna duda sobre las asignaciones de suscripción u otros aspectos del portal de administración, póngase en contacto con https://visualstudio.microsoft.com/subscriptions/support/ para obtener ayuda. 
