---
title: Asignación de licencias a suscripciones de Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 4e529a43-7aed-4eee-895d-862a631952df
ms.date: 03/02/2020
ms.topic: conceptual
description: Obtenga información sobre la manera en que los administradores pueden asignar licencias a los suscriptores.
ms.openlocfilehash: e8eba6ad97d0f5e7e1da0e75093c33658f26a56a
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/27/2020
ms.locfileid: "87235022"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Asignación de licencias en el Portal de administración de suscripciones de Visual Studio
Como administrador de suscripciones de Visual Studio, puede usar el Portal de administración para asignar suscripciones a usuarios y grupos de usuarios.

En el caso de grupos de usuarios, dispone de opciones para asignar suscripciones.  
- Puede asignar suscripciones de una en una.
- También puede cargar de forma rápida y sencilla listas de suscriptores y su información de suscripción mediante la característica para[agregar en masa](assign-license-bulk.md).
- Si su organización usa Microsoft Azure Active Directory (Azure AD), puede [usar grupos de Azure AD para asignar suscripciones](https://docs.microsoft.com/visualstudio/subscriptions/assign-license-bulk#use-azure-active-directory-groups-to-assign-subscriptions) a grupos de usuarios.  


## <a name="add-a-single-subscriber"></a>Adición de un solo suscriptor
Aquí se muestra cómo asignar una suscripción de Visual Studio a un nuevo usuario para que pueda acceder a los beneficios de la suscripción.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vpPh]


1. Inicie sesión en el [Portal de administración](https://manage.visualstudio.com).
2. Para asignar una licencia a un solo suscriptor de Visual Studio, seleccione **Agregar** en la parte superior de la tabla y, a continuación, seleccione **Suscriptor individual**.
   > [!div class="mx-imgBorder"]
   > ![Adición de un solo suscriptor](_img/assign-license-add/add-subscriber-individual.png "Haga clic en Agregar y seleccione Suscriptor individual para asignar una sola suscripción.")
3. Escriba la información en los campos del formulario para el nuevo suscriptor. Si su organización usa Azure Active Directory, el campo **Nombre** actúa como una función de búsqueda para buscar personas en el directorio actual, por lo que puede seleccionar el usuario de los resultados de la búsqueda. Después de seleccionar a esa persona, se rellenan automáticamente el correo electrónico de inicio de sesión y de notificación.
   > [!div class="mx-imgBorder"]
   > ![Detalles del suscriptor](_img/assign-license-add/subscriber-details.png "Escriba el nombre del suscriptor y otros detalles, o elija entre los miembros del inquilino.")

    > [!NOTE]
    > Para que los miembros de un inquilino de Azure Active Directory estén visibles cuando escriba un nombre de suscriptor, el administrador debe ser miembro del inquilino. 


    Si quiere que este suscriptor tenga acceso a las descargas de software cuando inicie sesión en el [portal de suscripciones de Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), asegúrese de dejar habilitadas las descargas en la sección **Configuración de descarga**. Si decide deshabilitar las descargas, el usuario no tendrá acceso a las descargas de software.  También se deshabilitará el acceso a las claves de producto.  El suscriptor seguirá teniendo acceso a todas las demás ventajas incluidas en la suscripción.
   > [!div class="mx-imgBorder"]
   > ![Acceso a las descargas](media/access-to-downloads.png "Seleccione Permitir para proporcionar al suscriptor acceso a las descargas de software.")

    Si quiere agregar sus propias notas de referencia a la suscripción, puede hacerlo en la sección **Agregar referencia**.
   > [!div class="mx-imgBorder"]
   > ![Adición de notas de referencia propias a cada suscripción](media/add-subscriber-reference-notes.png "Use el campo Referencia para registrar notas sobre esta suscripción.")

    Cuando haya terminado de seleccionar opciones y de especificar datos para el suscriptor, elija **Agregar** en la parte inferior de la ventana emergente **Agregar suscriptor**.
   > [!div class="mx-imgBorder"]
   > ![Elección del botón Agregar](media/add-button.png "Haga clic en Agregar para guardar la información y asignar la suscripción al suscriptor.")

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


