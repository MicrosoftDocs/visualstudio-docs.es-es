---
title: Roles de administrador y superadministrador en el portal de administración
author: evanwindom
ms.author: lank
manager: lank
ms.date: 08/21/2019
ms.topic: conceptual
description: Obtenga información sobre los roles de administrador y superadministrador y sobre la asignación de administradores.
ms.openlocfilehash: 1beda505008815b87a0de98ee597d7b5ec97693d
ms.sourcegitcommit: c90a998716b3dfa614dedc61a1bea515364efbec
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/23/2019
ms.locfileid: "70000945"
---
# <a name="super-admins-and-administrators-for-visual-studio-subscription-agreements"></a>Administradores y superadministradores para contratos de suscripción de Visual Studio

En el nuevo portal de administración de suscripciones de Visual Studio para clientes del programa de licencias por volumen hay dos roles distintos. Estos roles se asemejan al rol de contacto principal o para notificaciones y al rol de administrador de suscripciones que existían en VLSC.

**Superadministradores:** cuando se configura una organización por primera vez, el contacto principal o para notificaciones es de forma predeterminada el superadministrador. El contacto principal o el que recibe los avisos puede asignar superadministradores o administradores adicionales. Un superadministrador puede agregar y quitar otros administradores, así como suscriptores. Si hay más de dos superadministradores en el sistema, un superadministrador puede eliminarlos a todos menos a los dos últimos por razones de seguridad.

**Administradores:** solo un superadministrador puede asignar administradores. Un administrador solo puede administrar los suscriptores de los contratos que el superadministrador le asigne.

## <a name="assigning-administrators"></a>Asignación de administradores
Para asignar nuevos administradores:
1. Inicie sesión en https://manage.visualstudio.com con una dirección de correo electrónico asignada como superadministrador en el contrato a través del cual se adquirieron las suscripciones.
2. Haga clic en la pestaña etiquetada como **Administrar administradores**.
3. Haga clic en **Agregar**.
   > [!div class="mx-imgBorder"]
   > ![Adición de administradores](_img/admin-roles/add-admins.png)
4. Rellene el formulario con la información del nuevo administrador.  
   > [!div class="mx-imgBorder"]
   > ![Formulario para agregar un administrador](_img/admin-roles/add-form.png)

   > [!NOTE]
   > Si quiere que este administrador pueda asignar otros administradores, recuerde activar la casilla **Superadministrador**.

5. Cuando haga clic en **Agregar** para asignar el nuevo administrador, este recibirá un correo electrónico en el que se le invitará a iniciar sesión en el portal.  

## <a name="resources"></a>Recursos
- [Soporte técnico para suscripciones y administración de Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs)

## <a name="next-steps"></a>Pasos siguientes
- Descubra cómo [asignar suscripciones](assign-license.md).
- Obtenga más información sobre todas las [ventajas de suscripción](https://visualstudio.microsoft.com/vs/benefits/).
- [Establecimiento de las preferencias del contrato](admin-prefs.md) 


