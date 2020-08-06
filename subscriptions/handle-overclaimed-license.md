---
title: Administración de licencias sobreasignadas| Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: a747100c-6f08-41a4-aaad-05099741742b
ms.date: 03/03/2020
ms.topic: conceptual
description: Conozca cómo los administradores pueden resolver suscripciones sobreasignadas
ms.openlocfilehash: b518dc9300862e7c39af0489734734668097ef9f
ms.sourcegitcommit: b8ec700fc4c14c68c6ce280f29c19870261990d8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2020
ms.locfileid: "87453722"
---
# <a name="over-allocated-subscriptions"></a>Suscripciones con exceso de asignación
A veces los pedidos se cambian después de haber agregado a los suscriptores, lo que puede causar que en su empresa haya más suscriptores asignados que licencias en propiedad. Este hecho se conoce como "sobreasignación".  

Para ver las asignaciones de suscripción, haga clic en el icono superior de la izquierda para abrir el panel Asignaciones.  

> [!NOTE]
> No se permiten sobreasignaciones en programas de licencia abierta.  Además, otros programas pueden mostrar esta información en el portal de forma diferente.
>
> [!div class="mx-imgBorder"]
> ![Aviso de exceso de asignación de suscripciones](_img/over-claimed/over-claimed-alert.png "El número de sobreasignaciones se muestra en la información general y la barra con hash lo representa en el gráfico para cada tipo de suscripción.")

Observe que las suscripciones sobreasignadas se muestran con una barra desteñida.  En la sección de información general de la parte superior se indica el número de sobreasignaciones para todos los tipos de suscripción, y cada nivel de suscripción también muestra su propio estado de asignación.  

## <a name="resolve-over-allocated-subscriptions"></a>Resolución de las suscripciones sobreasignadas
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

## <a name="see-also"></a>Vea también
- [Documentación de Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentación de Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentación de Azure](https://docs.microsoft.com/azure/)
- [Documentación de Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Pasos siguientes
- Obtenga más información sobre cómo administrar [suscripciones de Visual Studio con GitHub Enterprise](assign-github.md).
- Para obtener ayuda con las ventas, las suscripciones, las cuentas y la facturación para suscripciones de Visual Studio, póngase en contacto con el [soporte para suscripciones](https://visualstudio.microsoft.com/subscriptions/support/) de Visual Studio.