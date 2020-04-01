---
title: Configuración los administradores de suscripciones mensuales | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 8b30e2bc-2ac3-4fcc-b296-128731471032
ms.date: 03/03/2020
ms.topic: conceptual
description: Configuración de los administradores de suscripciones mensuales
ms.openlocfilehash: c9a1303d4111f0ec4a0c1249a25e49fc40cf26de
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232652"
---
# <a name="set-up-administrators-for-visual-studio-monthly-subscriptions"></a>Configuración de los administradores de suscripciones mensuales de Visual Studio

Los administradores administran las suscripciones mensuales de Visual Studio. Estos usuarios pueden asignar, editar, agregar o eliminar suscripciones y realizar otras tareas de administración de suscripciones.

## <a name="the-azure-subscription-owner-is-the-first-administrator"></a>El propietario de la suscripción de Azure es el primer administrador

Al comprar suscripciones mensuales de Visual Studio, como propietario de la suscripción de Azure utilizada para realizar las compras, se le configura automáticamente como administrador para esas suscripciones.

Puede comprar suscripciones mensuales a través de [Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions) o de un proveedor de soluciones en la nube. Si compra a través de Visual Studio Marketplace, al final de la experiencia de compra, tendrá la oportunidad de administrar a los usuarios. Si elige esa opción, se le dirige al portal de administración de suscripciones de Visual Studio: [https://manage.visualstudio.com](https://manage.visualstudio.com).

Una vez que haya comprado suscripciones, puede visitar el [portal de administración](https://manage.visualstudio.com) en cualquier momento. Inicie sesión en el portal y seleccione la suscripción a Azure apropiada en la esquina superior izquierda.

Como propietario de la suscripción de Azure utilizada para comprar las suscripciones mensuales, también puede asignar a otros administradores.

## <a name="add-administrators"></a>Agregar administradores

Para agregar administradores:

1. Conéctese a Azure Portal en [portal.azure.com](https://portal.azure.com).
2. Inicie sesión con la cuenta que utilizó para comprar las suscripciones mensuales de Visual Studio.
3. En **Servicios de Azure**, seleccione **Administración de costos + facturación**.
   > [!div class="mx-imgBorder"]
   > ![Seleccionar Administración de costos + facturación en Servicios de Azure](_img/cloud-admin/azure-cost-billing.png)
4. En la lista **Mis suscripciones**, elija la suscripción de Azure que utilizó para realizar la compra.
   > [!div class="mx-imgBorder"]
   > ![Elección de la suscripción](_img/cloud-admin/subscription-list.png)
5. Haga clic en **Control de acceso (IAM)** , que se encuentra cerca de la parte superior de la lista en el panel de navegación izquierdo.
6. Haga clic en la pestaña **Agregar** en la parte superior de la página.
7. Haga clic en **Agregar asignación de roles**.
   > [!div class="mx-imgBorder"]
   > ![Seleccionar Control de acceso, Agregar, Agregar asignación de roles](_img/cloud-admin/access-control-add.png)
8. En el panel de la derecha, haga clic en el menú desplegable **Rol** de la parte superior, desplácese hacia abajo y seleccione **Administrador de acceso de usuarios**.
9. En la lista de usuarios, desplácese hasta el usuario que quiere convertir en administrador y selecciónelo. 
   > [!div class="mx-imgBorder"]
   > ![Seleccionar Rol, Administrador de acceso de usuarios](_img/cloud-admin/add-role-user-access-admin.png)
10. Haga clic en **Guardar**.
11. Haga clic en la pestaña **Asignaciones de roles** para comprobar que el usuario seleccionado aparece ahora como Administrador de acceso de usuario.

Ahora, el administrador nuevo puede iniciar sesión en el [portal de administración](https://manage.visualstudio.com), seleccionar la misma suscripción de Azure que se ha usado para comprar las suscripciones mensuales en la lista de la esquina superior izquierda de la página y comenzar a administrar esas suscripciones.

> [!NOTE]
> Si ve usuarios con acceso para editar sus suscripciones mensuales que no estableció como administradores, puede que tengan roles en la suscripción subyacente de Azure que les permitan administrar suscripciones. Estos roles son: propietario, colaborador, administrador de servicios o coadministrador. Para obtener más información, visite [Add billing managers](/azure/devops/organizations/billing/add-backup-billing-managers?view=vsts) (Agregar administradores de facturación).

Para obtener información sobre las suscripciones mensuales de Visual Studio, vea [Introducción](vscloud-overview.md) en Compra de suscripciones. Para comprar suscripciones mensuales de Visual Studio, visite Visual Studio Marketplace en [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription).

## <a name="see-also"></a>Vea también
- [Documentación de Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentación de Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentación de Azure](https://docs.microsoft.com/azure/)
- [Documentación de Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Pasos siguientes
Obtenga más información sobre la administración de suscripciones de Visual Studio.
- [Asignación de suscripciones individuales](assign-license.md)
- [Asignación de varias suscripciones](assign-license-bulk.md)
- [Editar suscripciones](edit-license.md)
- [Determinación del uso máximo](maximum-usage.md)



