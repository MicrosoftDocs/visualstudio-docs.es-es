---
title: Asignación de licencias a suscripciones de Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/02/2020
ms.topic: conceptual
description: Obtenga información sobre la manera en que los administradores pueden asignar licencias a los suscriptores.
ms.openlocfilehash: 3d444f930d1fab166d437911b5609caf75cad09e
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263321"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Asignación de licencias en el Portal de administración de suscripciones de Visual Studio
Como administrador de suscripciones de Visual Studio, puede usar el Portal de administración para asignar suscripciones a usuarios y grupos de usuarios.

En el caso de grupos de usuarios, dispone de opciones para asignar suscripciones.  
- Puede asignar suscripciones de una en una.
- También puede cargar de forma rápida y sencilla listas de suscriptores y su información de suscripción mediante la característica para[agregar en masa](assign-license-bulk.md).
- Si su organización usa Microsoft Azure Active Directory (Azure AD), puede usar grupos de Azure AD para asignar suscripciones a grupos de usuarios.  (Esta característica se implementa en fases y puede que no esté disponible de inmediato para su organización).


## <a name="add-a-single-subscriber"></a>Adición de un solo suscriptor
Aquí se muestra cómo asignar una suscripción de Visual Studio a un nuevo usuario para que pueda acceder a los beneficios de la suscripción.

1. Inicie sesión en el [Portal de administración](https://manage.visualstudio.com).
2. Para asignar una licencia a un solo suscriptor de Visual Studio, seleccione **Agregar** en la parte superior de la tabla y, a continuación, seleccione **Suscriptor individual**.
   > [!div class="mx-imgBorder"]
   > ![Adición de un solo suscriptor](_img/assign-license-add/add-subscriber-individual.png)
3. Escriba la información en los campos del formulario para el nuevo suscriptor. Si su organización usa Azure Active Directory, el campo **Nombre** actúa como una función de búsqueda para buscar personas en el directorio actual, por lo que puede seleccionar el usuario de los resultados de la búsqueda. Después de seleccionar a esa persona, se rellenan automáticamente el correo electrónico de inicio de sesión y de notificación.
   > [!div class="mx-imgBorder"]
   > ![Detalles del suscriptor](_img/assign-license-add/subscriber-details.png)

    Si quiere que este suscriptor tenga acceso a las descargas de software cuando inicie sesión en el [portal de suscripciones de Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), asegúrese de dejar habilitadas las descargas en la sección **Configuración de descarga**. Si elije deshabilitar las descargas, el usuario no tendrá acceso a las descargas de software, pero seguirá teniendo acceso a todas las demás ventajas incluidas en la suscripción.
   > [!div class="mx-imgBorder"]
   > ![Acceso a las descargas](media/access-to-downloads.png)

    Si quiere agregar sus propias notas de referencia a la suscripción, puede hacerlo en la sección **Agregar referencia**.
   > [!div class="mx-imgBorder"]
   > ![Adición de notas de referencia propias a cada suscripción](media/add-subscriber-reference-notes.png)

    Cuando haya terminado de seleccionar opciones y de especificar datos para el suscriptor, elija **Agregar** en la parte inferior de la ventana emergente **Agregar suscriptor**.
   > [!div class="mx-imgBorder"]
   > ![Elección del botón Agregar](media/add-button.png)

## <a name="resend-assignment-emails"></a>Reenvío de correos electrónicos de asignación
Después de agregar un suscriptor, se envía automáticamente un correo electrónico de asignación al nuevo suscriptor con más instrucciones. Puede volver a enviar el correo electrónico de asignación en cualquier momento si selecciona el suscriptor y hace clic en el botón **Reenviar** en el menú superior.  Para reenviar correos electrónicos a varios usuarios, mantenga presionada la tecla **Ctrl** mientras selecciona los suscriptores.  Al hacer clic en el botón **Reenviar**, verá un cuadro de diálogo que le pedirá que confirme que desea volver a enviar a los suscriptores.  

## <a name="see-also"></a>Vea también
- [Documentación de Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentación de Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentación de Azure](https://docs.microsoft.com/azure/)
- [Documentación de Microsoft 365](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>Pasos siguientes
- ¿Tiene que agregar muchos usuarios?  Aprenda a asignar suscripciones a [varios suscriptores](assign-license-bulk.md).
- ¿Necesita ayuda?  Póngase en contacto con el [soporte técnico de administración y suscripciones de Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).


