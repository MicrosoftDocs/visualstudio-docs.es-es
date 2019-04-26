---
title: Configurar los administradores de suscripciones de nube | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 03/28/2018
ms.topic: conceptual
description: Configurar los administradores de suscripciones de nube
searchscope: VS Subscription
ms.openlocfilehash: 34479c21ec3cb0672b8d2354595c971b062bba56
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945827"
---
# <a name="set-up-administrators-for-visual-studio-cloud-subscriptions"></a>Configurar los administradores de suscripciones de nube de Visual Studio

Los administradores administran las suscripciones de nube de Visual Studio. Estos usuarios pueden asignar, editar, agregar o eliminar suscripciones y realizar otras tareas de administración de suscripciones.

## <a name="the-azure-subscription-owner-is-the-first-administrator"></a>El propietario de la suscripción de Azure es el primer administrador

Al comprar suscripciones de nube de Visual Studio, como propietario de la suscripción de Azure utilizada para realizar las compras, se le configura automáticamente como administrador para esas suscripciones.

Puede comprar suscripciones de nube a través de [Visual Studio Marketplace](https://marketplace.visualstudio.com/subscriptions) o de un proveedor de soluciones en la nube. Si compra a través de Visual Studio Marketplace, al final de la experiencia de compra, tendrá la oportunidad de administrar a los usuarios. Si elige esa opción, se le dirigirá al portal de administración de suscripciones de Visual Studio: [https://manage.visualstudio.com](https://manage.visualstudio.com).

Una vez que haya comprado suscripciones, puede visitar el [portal de administración](https://manage.visualstudio.com) en cualquier momento. Inicie sesión en el portal y seleccione la suscripción a Azure apropiada en la esquina superior izquierda.

Como propietario de la suscripción de Azure utilizada para comprar las suscripciones de nube, también puede asignar a otros administradores.

## <a name="add-administrators"></a>Agregar administradores

Para agregar administradores:

1. Conéctese a Azure Portal en [portal.azure.com](https://portal.azure.com).
2. Inicie sesión con la cuenta que utilizó para comprar las suscripciones de nube de Visual Studio.
3. En el panel de navegación izquierdo, desplácese hacia abajo hasta **Administración de costos + facturación**.
4. En la lista **Mis suscripciones**, elija la suscripción de Azure que utilizó para realizar la compra.
5. Haga clic en **Control de acceso**, que se encuentra cerca de la parte superior de la lista en el panel de navegación izquierdo.
6. Haga clic en la pestaña **Agregar** en la parte superior de la página.
7. En el panel emergente de la derecha, haga clic en el nombre del suscriptor que quiera convertir en administrador.
8. Haga clic en el menú desplegable **Rol** en la parte superior del panel, desplácese hacia abajo y seleccione **Administrador de acceso de usuarios**.
9. Haga clic en **Guardar**.

El suscriptor que ha designado aparece en el centro de la página y su rol se muestra como "Administrador de acceso de usuario".

Ahora, el administrador nuevo puede iniciar sesión en el [portal de administración](https://manage.visualstudio.com), seleccionar la misma suscripción de Azure que se utilizó para comprar las suscripciones de nube en la lista de la esquina superior izquierda de la página y comenzar a administrar esas suscripciones.

> [!NOTE]
> Si ve usuarios con acceso para editar sus suscripciones de nube que no estableció como administradores, puede que tengan roles en la suscripción subyacente de Azure que les permitan administrar suscripciones. Estos roles son: propietario, colaborador, administrador de servicios o coadministrador. Para obtener más información, visite [Add billing managers](/azure/devops/organizations/billing/add-backup-billing-managers?view=vsts) (Agregar administradores de facturación).

Para obtener información sobre las suscripciones de nube de Visual Studio, consulte [Introducción](vscloud-overview.md) en Compra de suscripciones de nube. Para comprar suscripciones de nube de Visual Studio, visite Visual Studio Marketplace en [https://marketplace.visualstudio.com/subscriptions](https://marketplace.visualstudio.com/subscription).