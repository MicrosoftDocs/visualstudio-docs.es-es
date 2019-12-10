---
title: Asignación de licencias a suscripciones de Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Obtenga información sobre la manera en que los administradores pueden asignar licencias a los suscriptores.
ms.openlocfilehash: 8785d4d4253fa3217341c8200a94dab923ae4a5f
ms.sourcegitcommit: af9bbf9116a63c0631ff2f4f3a878564aa63cd8c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2019
ms.locfileid: "74797373"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Asignación de licencias en el Portal de administración de suscripciones de Visual Studio
Como administrador de suscripciones de Visual Studio, puede usar el Portal de administración para asignar suscripciones a usuarios y grupos de usuarios.

Puede asignar suscripciones a grupos de usuarios de una en una o usar la característica [Agregar en masa](assign-license-bulk.md) para cargar rápida y fácilmente listas de suscriptores con su información de suscripción.

## <a name="add-a-single-subscriber"></a>Adición de un solo suscriptor
Aquí se muestra cómo asignar una licencia de suscripciones de Visual Studio a un nuevo usuario para que pueda acceder a los beneficios de la suscripción.

1. Inicie sesión en el [Portal de administración](https://manage.visualstudio.com).
2. Para asignar una licencia a un solo suscriptor de Visual Studio, seleccione **Agregar** en la parte superior de la tabla.
   > [!div class="mx-imgBorder"]
   > ![Adición de un solo suscriptor](media/add-single-subscriber.png)
3. Escriba la información en los campos del formulario para el nuevo suscriptor. Si su organización usa Azure Active Directory, el campo **Nombre** actúa como una función de búsqueda para buscar personas en el directorio actual, por lo que puede seleccionar el usuario de los resultados de la búsqueda. Después de seleccionar a esa persona, se rellenan automáticamente el correo electrónico de inicio de sesión y de notificación.
   > [!div class="mx-imgBorder"]
   > ![Detalles del suscriptor](_img/assign-license-add/subscriber-details.png)

    Si quiere que este suscriptor tenga acceso a las descargas de software cuando inicie sesión en el [portal de suscripciones de Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), asegúrese de dejar habilitadas las descargas en la sección **Configuración de descarga**. Si elije deshabilitar las descargas, el usuario no tendrá acceso a las descargas de software, pero seguirá teniendo acceso a todas las demás ventajas incluidas en la suscripción.
   > [!div class="mx-imgBorder"]
   > ![Acceso a las descargas](media/access-to-downloads.png)

       If you'd like to add your own reference notes to the subscription, you can do so in the **Add reference** section.
   > [!div class="mx-imgBorder"]
   > ![Adición de notas de referencia propias a cada suscripción](media/add-subscriber-reference-notes.png)

    Cuando haya terminado de seleccionar opciones y de especificar datos para el suscriptor, elija **Agregar** en la parte inferior de la ventana emergente **Agregar suscriptor**.
   > [!div class="mx-imgBorder"]
   > ![Elección del botón Agregar](media/add-button.png)

## <a name="resend-assignment-emails"></a>Reenvío de correos electrónicos de asignación
Después de agregar un suscriptor, se envía automáticamente un correo electrónico de asignación al nuevo suscriptor con más instrucciones. Puede volver a enviar el correo electrónico de asignación en cualquier momento si selecciona el suscriptor y hace clic en el botón **Reenviar** en el menú superior.  Para reenviar correos electrónicos a varios usuarios, mantenga presionada la tecla **Ctrl** mientras selecciona los suscriptores.  Al hacer clic en el botón **Reenviar**, verá un cuadro de diálogo que le pedirá que confirme que desea volver a enviar a los suscriptores.  

## <a name="next-steps"></a>Pasos siguientes
- ¿Tiene que agregar muchos usuarios?  Aprenda a asignar suscripciones a [varios suscriptores](assign-license-bulk.md).
- ¿Necesita ayuda?  Póngase en contacto con el [soporte técnico de administración y suscripciones de Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs).

