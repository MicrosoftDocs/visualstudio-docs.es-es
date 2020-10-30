---
title: Roles de administrador y superadministrador para las suscripciones de Visual Studio
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 6601c395-f778-48c1-ab76-cf454b9193e4
ms.date: 10/22/2020
ms.topic: conceptual
description: Obtenga información sobre los roles de administrador y superadministrador y sobre cómo asignar los administradores.
ms.openlocfilehash: 491a8de27477f68b4344ad17b860b80b4ca96aa9
ms.sourcegitcommit: bf5e2bba5acdcf05869b861211f8bb755081e5ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2020
ms.locfileid: "92467380"
---
# <a name="super-admins-and-admins-for-visual-studio-subscription-agreements"></a>Administradores y superadministradores para contratos de suscripción de Visual Studio

En el nuevo portal de administración de suscripciones de Visual Studio para clientes del programa de licencias por volumen hay dos roles distintos. Estos roles se asemejan al rol de contacto principal o para notificaciones y al rol de administrador de suscripciones que existían en VLSC.

**Superadministradores:** cuando se configura una organización por primera vez, el contacto principal o para notificaciones es de forma predeterminada el superadministrador. El contacto principal o el que recibe los avisos puede asignar superadministradores o administradores adicionales. Un superadministrador puede agregar y quitar otros administradores, así como suscriptores. Si hay más de dos superadministradores en el sistema, un superadministrador puede eliminarlos a todos menos a los dos últimos por razones de seguridad.

**Administradores:** solo un superadministrador puede asignar administradores. Un administrador solo puede administrar los suscriptores de los contratos que el superadministrador le asigne.

Vea una demostración sobre cómo administrar administradores. 
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6L]

## <a name="assigning-admins"></a>Asignación de administradores
Para asignar administradores nuevos (administradores):
1. Inicie sesión en https://manage.visualstudio.com con una dirección de correo electrónico asignada como superadministrador en el contrato a través del cual se adquirieron las suscripciones.
2. Haga clic en la pestaña etiquetada como **Administrar administradores** .
3. Haga clic en **Agregar** .
   > [!div class="mx-imgBorder"]
   > ![Agregar administradores](_img/admin-roles/add-admins.png "Haga clic en la hoja Administrar administradores y en Agregar para asignar nuevos administradores.")
4. Rellene el formulario con la información del nuevo administrador.  
   > [!div class="mx-imgBorder"]
   > ![Formulario Agregar administrador](_img/admin-roles/add-form.png "Especifique la información de inicio de sesión del nuevo administrador y decida si quiere convertirlo en superadministrador.  Luego, haga clic en Agregar.")

   > [!NOTE]
   > Si quiere que este administrador pueda asignar otros administradores, recuerde activar la casilla **Superadministrador** .

5. Cuando haga clic en **Agregar** para asignar el nuevo administrador, este recibirá un correo electrónico en el que se le invitará a iniciar sesión en el portal.  

## <a name="resources"></a>Recursos
- [Soporte técnico para suscripciones y administración de Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs)

## <a name="see-also"></a>Vea también
- [Documentación de Visual Studio](/visualstudio/)
- [Documentación de Azure DevOps](/azure/devops/)
- [Documentación de Azure](/azure/)
- [Documentación de Microsoft 365](/microsoft-365/)


## <a name="next-steps"></a>Pasos siguientes
- Descubra cómo [asignar suscripciones](assign-license.md).
- Obtenga más información sobre todas las [ventajas de suscripción](https://visualstudio.microsoft.com/vs/benefits/).
- [Establecimiento de las preferencias del contrato](admin-prefs.md)