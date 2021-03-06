---
title: Configuración de los administradores de suscripciones de Visual Studio mensuales | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 8b30e2bc-2ac3-4fcc-b296-128731471032
ms.date: 03/21/2021
ms.topic: how-to
description: Configuración de los administradores de suscripciones mensuales
ms.openlocfilehash: 220f5986bb06b638504379b63e911f9bb62926b5
ms.sourcegitcommit: d7d9fb79448b3534923cc95071d1f91eabde88e8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104776953"
---
# <a name="set-up-admins-for-visual-studio-monthly-subscriptions"></a>Configuración de los administradores de suscripciones mensuales de Visual Studio

Los administradores administran las suscripciones mensuales de Visual Studio. Estos usuarios pueden asignar, editar, agregar o eliminar suscripciones y realizar otras tareas de administración de suscripciones.

## <a name="the-azure-subscription-owner-is-the-first-admin"></a>El propietario de la suscripción de Azure es el primer administrador

Al comprar suscripciones mensuales de Visual Studio, como propietario de la suscripción de Azure utilizada para realizar las compras, se le configura automáticamente como administrador para esas suscripciones.

Puede comprar suscripciones mensuales a través de [Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions) o de un proveedor de soluciones en la nube. Si compra a través de Visual Studio Marketplace, al final de la experiencia de compra, tendrá la oportunidad de administrar a los usuarios. Si elige esa opción, se le dirige al portal de administración de suscripciones de Visual Studio: [https://manage.visualstudio.com](https://manage.visualstudio.com).

Una vez que haya comprado suscripciones, puede visitar el [portal de administración](https://manage.visualstudio.com) en cualquier momento. Inicie sesión en el portal y seleccione la suscripción a Azure apropiada en la esquina superior izquierda.

Como propietario de la suscripción de Azure utilizada para comprar las suscripciones mensuales, también puede asignar a otros administradores.

## <a name="add-admins"></a>Agregar administradores

Para agregar administradores:

1. Conéctese a Azure Portal en [portal.azure.com](https://portal.azure.com).
2. Inicie sesión con la cuenta que utilizó para comprar las suscripciones mensuales de Visual Studio.
3. En **Servicios de Azure**, seleccione **Administración de costos + facturación**.
   > [!div class="mx-imgBorder"]
   > ![Seleccionar Administración de costos + facturación en Servicios de Azure](_img/cloud-admin/azure-cost-billing.png "Elija Cost Management en el grupo de servicios de Azure.")
4. En la lista **Mis suscripciones**, elija la suscripción de Azure que utilizó para realizar la compra.
   > [!div class="mx-imgBorder"]
   > ![Elección de la suscripción](_img/cloud-admin/subscription-list.png "Elija la suscripción de Azure que desea usar para realizar la compra.")
5. Haga clic en **Control de acceso (IAM)** , que se encuentra cerca de la parte superior de la lista en el panel de navegación izquierdo.
6. Haga clic en la pestaña **Agregar** en la parte superior de la página.
7. Haga clic en **Agregar asignación de roles**.
   > [!div class="mx-imgBorder"]
   > ![Seleccionar Control de acceso, Agregar, Agregar asignación de roles](_img/cloud-admin/access-control-add.png "Elija Control de acceso en la lista de la izquierda y, a continuación, elija Agregar.")
8. En el panel de la derecha, haga clic en el menú desplegable **Rol** de la parte superior, desplácese hacia abajo y seleccione **Administrador de acceso de usuarios**.
9. En la lista de usuarios, desplácese hasta el usuario que quiere convertir en administrador y selecciónelo. 
   > [!div class="mx-imgBorder"]
   > ![Seleccionar Rol, Administrador de acceso de usuarios](_img/cloud-admin/add-role-user-access-admin.png "Elija Rol, seleccione Administrador de acceso de usuario y, a continuación, seleccione el nombre del usuario para que sea administrador.")
10. Haga clic en **Guardar**.
11. Haga clic en la pestaña **Asignaciones de roles** para comprobar que el usuario seleccionado aparece ahora como Administrador de acceso de usuario.

Ahora, el administrador nuevo puede iniciar sesión en el [portal de administración](https://manage.visualstudio.com), seleccionar la misma suscripción de Azure que se ha usado para comprar las suscripciones mensuales en la lista de la esquina superior izquierda de la página y comenzar a administrar esas suscripciones.

> [!NOTE]
> Si ve usuarios con acceso para editar sus suscripciones mensuales que no estableció como administradores, puede que tengan roles en la suscripción subyacente de Azure que les permitan administrar suscripciones. Estos roles son: propietario, colaborador, administrador de servicios o coadministrador. Para obtener más información, visite [Add billing managers](/azure/devops/organizations/billing/add-backup-billing-managers) (Agregar administradores de facturación).

Para obtener información sobre las suscripciones mensuales de Visual Studio, vea [Introducción](vscloud-overview.md) en Compra de suscripciones. Para comprar suscripciones mensuales de Visual Studio, visite Visual Studio Marketplace en [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription).

## <a name="resources"></a>Recursos
- [Soporte de la suscripción de Visual Studio](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Consulte también
- [Documentación de Visual Studio](/visualstudio/)
- [Documentación de Azure DevOps](/azure/devops/)
- [Documentación de Azure](/azure/)
- [Documentación de Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Pasos siguientes
Obtenga más información sobre la administración de suscripciones de Visual Studio.
- [Asignación de suscripciones individuales](assign-license.md)
- [Asignación de varias suscripciones](assign-license-bulk.md)
- [Editar suscripciones](edit-license.md)
- [Determinación del uso máximo](maximum-usage.md)