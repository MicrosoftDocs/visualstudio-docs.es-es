---
title: Administración de licencias con exceso de asignación| Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 02/13/2018
ms.topic: conceptual
description: Obtenga información sobre cómo los administradores pueden resolver el exceso de asignación de suscripciones
ms.openlocfilehash: 23a0888a670c10af4447d7a097067ffe4fe70c0f
ms.sourcegitcommit: 208395bc122f8d3dae3f5e5960c42981cc368310
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783448"
---
# <a name="overallocated-subscriptions"></a>Suscripciones con exceso de asignación

A veces los pedidos se cambian después de haber agregado a los suscriptores, lo que puede causar que en su empresa haya más suscriptores asignados que licencias en propiedad. Cuando esto ocurre, en la pestaña Suscriptores se muestra una alerta y se proporciona más información.

> [!NOTE]
> No se permiten los escenarios de exceso de asignación en programas de licencia abierta.  Además, otros programas pueden mostrar esta información en el portal de forma diferente.
>
> [!div class="mx-imgBorder"]
> ![Aviso de exceso de asignación de suscripciones](_img/over-claimed/over-claimed-alert.png)

## <a name="resolving-overallocated-subscriptions"></a>Resolución de suscripciones con exceso de asignación

Para resolver las licencias con exceso de asignación:

1. Haga clic en el texto de alerta. Se mostrará una lista filtrada de los suscriptores asignados al nivel de suscripción y la fecha de expiración del exceso de asignación. 

2. Quite suscriptores según sea necesario para corregir el exceso de asignación de licencias. 

3. La información general incluida en la parte izquierda de la página se actualizará para mostrar que vuelve a cumplir los requisitos, y todas las notificaciones sobre exceso de asignación desaparecerán. 

## <a name="billing-and-true-up"></a>Facturación y "true-up"

Si su organización tiene un contrato Enterprise (EA), los administradores pueden asignar suscripciones sin necesidad de adquirirlas y pagarlas más adelante a través de un proceso de reconciliación conocido como "true-up".  Cuando se produce un exceso de asignación, se facturará a su organización el número máximo de suscripciones asignadas a los usuarios durante el "true-up".  Esto se realiza incluso aunque ya no tenga el número máximo de suscripciones asignadas en el momento en que se lleve a cabo el "true-up".  Para obtener más información sobre cómo supervisar el uso máximo, visite el tema [Uso máximo](maximum-usage.md).

> [!Important]
> Si las suscripciones de Visual Studio con GitHub Enterprise son asignadas por administradores de suscripciones de Visual Studio y nunca se han comprado estas suscripciones, no serán visibles para los administradores de GitHub Enterprise de la organización. Para asegurarse de que las suscripciones de GitHub Enterprise sean visibles, debe realizarse una compra que incluya **como mínimo una** suscripción de Visual Studio Professional con GitHub Enterprise o de Visual Studio Enterprise con GitHub Enterprise la primera vez que se asignen las suscripciones.  
>
> Es responsabilidad del cliente asegurarse de que para cada suscripción de GitHub que se asigne haya una suscripción de Visual Studio con GitHub correspondiente asignada en el portal de administración para seguir cumpliendo los requisitos de licencia para esta suscripción.

Obtenga más información sobre cómo administrar [suscripciones de Visual Studio con GitHub Enterprise](assign-github.md).

## <a name="support-resources"></a>Recursos de soporte técnico

- Para obtener ayuda con las ventas, las suscripciones, las cuentas y la facturación para suscripciones de Visual Studio, póngase en contacto con el [soporte para suscripciones](https://visualstudio.microsoft.com/subscriptions/support/) de Visual Studio.
