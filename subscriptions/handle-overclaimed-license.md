---
title: Administración de licencias sobreasignadas| Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Conozca cómo los administradores pueden resolver suscripciones sobreasignadas
ms.openlocfilehash: 924f6fb2c513d70aefd28c1d4ff18d1af62178c2
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605509"
---
# <a name="overallocated-subscriptions"></a>Suscripciones con exceso de asignación
A veces los pedidos se cambian después de haber agregado a los suscriptores, lo que puede causar que en su empresa haya más suscriptores asignados que licencias en propiedad. Este hecho se conoce como "sobreasignación".  Cuando esto sucede, en la pestaña Suscriptores se muestra una alerta y se proporciona información adicional acerca de cuántas suscripciones se han sobreasignado.

> [!NOTE]
> No se permiten sobreasignaciones en programas de licencia abierta.  Además, otros programas pueden mostrar esta información en el portal de forma diferente.
>
> [!div class="mx-imgBorder"]
> ![Aviso de exceso de asignación de suscripciones](_img/over-claimed/over-claimed-alert.png)

## <a name="resolve-overallocated-subscriptions"></a>Resolución de las suscripciones sobreasignadas
Hay varias maneras de resolver las sobreasignaciones:
- Póngase en contacto con su revendedor para adquirir suscripciones adicionales.
- Espere a su período anual de true-up y pague las suscripciones sobreasignadas en ese momento. 
- Elimine algunas asignaciones de suscripciones.  (Esto no le quitará de pagar en el período true-up anual dado que este período se basa en el número máximo de suscripciones asignadas en ese momento durante el año).

## <a name="billing-and-true-up"></a>Facturación y "true-up"
Si su organización tiene un contrato Enterprise (EA), los administradores pueden asignar suscripciones sin necesidad de adquirirlas y pagarlas más adelante a través de un proceso de reconciliación conocido como "true-up".  Cuando se produce un exceso de asignación, se facturará a su organización el número máximo de suscripciones asignadas a los usuarios durante el "true-up".  Esto se realiza incluso aunque ya no tenga el número máximo de suscripciones asignadas en el momento en que se lleve a cabo el "true-up".  Para obtener más información sobre cómo supervisar el uso máximo, visite el tema [Uso máximo](maximum-usage.md).

> [!Important]
> Si las suscripciones de Visual Studio con GitHub Enterprise son asignadas por administradores de suscripciones de Visual Studio y nunca se han comprado estas suscripciones, no serán visibles para los administradores de GitHub Enterprise de la organización. Para asegurarse de que las suscripciones de GitHub Enterprise sean visibles, debe realizarse una compra que incluya **como mínimo una** suscripción de Visual Studio Professional con GitHub Enterprise o de Visual Studio Enterprise con GitHub Enterprise la primera vez que se asignen las suscripciones.
>
> Es responsabilidad del cliente asegurarse de que para cada suscripción de GitHub que se asigne haya una suscripción de Visual Studio con GitHub correspondiente asignada en el portal de administración para seguir cumpliendo los requisitos de licencia para esta suscripción.

## <a name="next-steps"></a>Pasos siguientes
- Obtenga más información sobre cómo administrar [suscripciones de Visual Studio con GitHub Enterprise](assign-github.md).
- Para obtener ayuda con las ventas, las suscripciones, las cuentas y la facturación para suscripciones de Visual Studio, póngase en contacto con el [soporte para suscripciones](https://visualstudio.microsoft.com/subscriptions/support/) de Visual Studio.
