---
title: Asignación de suscripciones de Visual Studio a los usuarios | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 4e529a43-7aed-4eee-895d-862a631952df
ms.date: 09/21/2020
ms.topic: conceptual
description: Obtenga información sobre la manera en que los administradores pueden asignar licencias a los suscriptores.
ms.openlocfilehash: dd80a14a3ff57100f210fd7ae1b882c0ab7a9faf
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915419"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Asignación de licencias en el Portal de administración de suscripciones de Visual Studio
Como administrador de suscripciones de Visual Studio, puede usar el Portal de administradores para asignar suscripciones a usuarios y grupos de usuarios.

En el caso de grupos de usuarios, dispone de opciones para asignar suscripciones.  
- Puede asignar suscripciones de una en una.
- También puede cargar de forma rápida y sencilla listas de suscriptores y su información de suscripción mediante la característica para[agregar en masa](assign-license-bulk.md).
- Si su organización usa Microsoft Azure Active Directory (Azure AD), puede [usar grupos de Azure AD para asignar suscripciones](./assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) a grupos de usuarios.  


## <a name="add-a-single-subscriber"></a>Adición de un solo suscriptor
Vea el vídeo o siga leyendo para saber cómo asignar una suscripción de Visual Studio a un nuevo usuario para que pueda acceder a las ventajas de la suscripción.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vpPh]


1. Inicie sesión en el [portal de administradores](https://manage.visualstudio.com).
2. Para asignar una licencia a un solo suscriptor de Visual Studio, seleccione **Agregar** en la parte superior de la tabla y, a continuación, seleccione **Suscriptor individual**.
   > [!div class="mx-imgBorder"]
   > ![Adición de un solo suscriptor](_img/assign-license-add/add-subscriber-individual.png "Seleccione Agregar y luego Suscriptor individual para asignar una sola suscripción.")
3. Escriba la información en los campos del formulario para el nuevo suscriptor. Si su organización usa Azure Active Directory, el campo **Nombre** actúa como una función de búsqueda para buscar personas en el directorio actual, por lo que puede seleccionar el usuario de los resultados de la búsqueda. Después de seleccionar a esa persona, se rellenan automáticamente el correo electrónico de inicio de sesión y de notificación.  Si el suscriptor no se encuentra en la organización, el correo electrónico de notificación no se rellenará de forma automática, pero estará disponible para que agregue manualmente otra dirección de correo electrónico a la que se enviarán los correos electrónicos relacionados con la suscripción.  Si el servicio de correo electrónico bloquea los correos electrónicos entrantes en las direcciones de correo electrónico de inicio de sesión, es importante especificar otra dirección de correo electrónico de notificación para que los suscriptores y administradores reciban correos electrónicos importantes relacionados con la suscripción de Microsoft.
   > [!div class="mx-imgBorder"]
   > ![Detalles del suscriptor](_img/assign-license-add/subscriber-details.png "Escriba el nombre del suscriptor y otros detalles, o elija entre los miembros del inquilino.")

    > [!NOTE]
    > Para que los miembros de un inquilino de Azure Active Directory estén visibles cuando escriba un nombre de suscriptor, el administrador debe ser miembro del inquilino. 


    Si quiere que este suscriptor tenga acceso a las descargas de software cuando inicie sesión en el [portal de suscripciones de Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), asegúrese de dejar habilitadas las descargas en la sección **Configuración de descarga**. Si decide deshabilitar las descargas, el usuario no tendrá acceso a las descargas de software.  También se deshabilitará el acceso a las claves de producto.  El suscriptor seguirá teniendo acceso a todas las demás ventajas incluidas en la suscripción.
   > [!div class="mx-imgBorder"]
   > ![Acceso a las descargas](media/access-to-downloads.png "Elija "Permitir" para proporcionar al suscriptor acceso a las descargas de software.")

    Si quiere agregar sus propias notas de referencia a la suscripción, puede hacerlo en la sección **Agregar referencia**.
   > [!div class="mx-imgBorder"]
   > ![Adición de notas de referencia propias a cada suscripción](media/add-subscriber-reference-notes.png "Use el campo Referencia para registrar notas sobre esta suscripción.")

    Cuando haya terminado de seleccionar opciones y de especificar datos para el suscriptor, elija **Agregar** en la parte inferior de la ventana emergente **Agregar suscriptor**.
   > [!div class="mx-imgBorder"]
   > ![Elección del botón Agregar](media/add-button.png "Seleccione Agregar para guardar la información y asignar la suscripción al suscriptor.")

## <a name="why-use-a-different-notification-email-address"></a>¿Por qué usar otra dirección de correo electrónico de notificación?
Algunas organizaciones configuran sus servicios de correo electrónico para bloquear los mensajes entrantes de otros dominios.  El bloqueo de los mensajes de correo electrónico entrantes significa que los suscriptores y administradores perderán comunicaciones importantes:
- Los suscriptores no recibirán una notificación de que se les ha asignado una suscripción.  Esto también les impedirá activar algunas de las ventajas incluidas.  
- Los suscriptores a los que se les hayan asignado suscripciones de Visual Studio con GitHub Enterprise no recibirán la invitación para unirse a la organización de GitHub, lo que significa que no podrán aceptarla. **Tienen que aceptar la invitación enviada por correo electrónico** para obtener acceso a la organización de GitHub. 
- No se notificará a los administradores cuando se agreguen a un contrato, ni recibirán instrucciones de administración mensuales o notificaciones de cambios de características que afecten al modo en que administran las suscripciones.

El uso de una dirección de correo electrónico de notificación le proporciona la opción de permitir que los suscriptores reciban comunicaciones importantes sobre sus suscripciones sin cambiar la funcionalidad de sus direcciones de correo electrónico de inicio de sesión.  

## <a name="resend-assignment-emails"></a>Reenvío de correos electrónicos de asignación
Después de agregar un suscriptor, se envía automáticamente un correo electrónico de asignación al nuevo suscriptor con más instrucciones. Puede volver a enviar el correo electrónico de asignación en cualquier momento. Para ello, seleccione el suscriptor y el botón **Reenviar** en el menú superior.  Para reenviar correos electrónicos a varios usuarios, mantenga presionada la tecla **Ctrl** mientras selecciona los suscriptores.  Al seleccionar **Reenviar**, verá un cuadro de diálogo que le pedirá que confirme que quiere volver a enviar a los suscriptores.  



## <a name="see-also"></a>Vea también
- [Documentación de Visual Studio](/visualstudio/)
- [Documentación de Azure DevOps](/azure/devops/)
- [Documentación de Azure](/azure/)
- [Documentación de Microsoft 365](/microsoft-365/)


## <a name="next-steps"></a>Pasos siguientes
- ¿Tiene que agregar muchos usuarios?  Aprenda a asignar suscripciones a [varios suscriptores](assign-license-bulk.md).
- ¿Necesita ayuda?  Póngase en contacto con el [soporte técnico de administración y suscripciones de Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).