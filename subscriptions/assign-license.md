---
title: Asignar licencias a suscripciones de Visual Studio | Microsoft Docs
author: TerryGLee
ms.author: tglee
manager: douge
ms.date: 07/16/2018
ms.topic: conceptual
description: Obtenga información sobre la manera en que los administradores pueden asignar licencias a los suscriptores.
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 5307f05d39ca751453e73147cc08115bf8b9dd1a
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636800"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administrator-portal"></a>Asignar licencias en el portal de administradores de suscripciones de Visual Studio

Como administrador de suscripciones de Visual Studio, puede usar el portal de administradores para asignar suscripciones a usuarios individuales y grupos de usuarios.

Puede asignar suscripciones a grupos de usuarios de una en una o usar la característica **Agregar en masa** para cargar rápida y fácilmente listas de suscriptores con su información de suscripción.

## <a name="individual-assignments"></a>Asignaciones individuales

Aquí se muestra cómo asignar una licencia de suscripciones de Visual Studio a un nuevo usuario para que pueda acceder a los beneficios de la suscripción.

1. Inicie sesión en el [portal de administradores](https://manage.visualstudio.com).

2. Para asignar una licencia a un solo suscriptor de Visual Studio, seleccione **Agregar** en la parte superior de la tabla.
    > [!div class="mx-imgBorder"]
    > ![Adición de un solo suscriptor](media\add-single-subscriber.png)

3. Escriba la información en los campos del formulario para el nuevo suscriptor. Si su organización usa Azure Active Directory, este campo actúa como una función de búsqueda para buscar personas en el directorio actual, por lo que puede seleccionar el usuario correcto entre los resultados de la búsqueda. Una vez que haya seleccionado a esa persona, se rellenan automáticamente su nombre, correo electrónico de inicio de sesión y correo electrónico de notificación.
    > [!div class="mx-imgBorder"]
    > ![Adición de una nueva dirección de correo electrónico de notificación](media\add-new-subscriber-notification-email.png)

    Si quiere que este suscriptor tenga acceso a las descargas de software cuando inicie sesión en el [portal de suscripciones de Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), asegúrese de dejar habilitadas las descargas en la sección **Configuración de descarga**. Si elije deshabilitar las descargas, el usuario no tendrá acceso a las descargas de software, pero seguirá teniendo acceso a todas las demás ventajas incluidas en la suscripción.
    > [!div class="mx-imgBorder"]
    > ![Acceso a las descargas](media\access-to-downloads.png)

    Si quiere cambiar el idioma en el que el suscriptor recibe información, puede hacerlo en la sección **Preferencias de comunicación**.
    > [!div class="mx-imgBorder"]
    > ![Cambio del idioma que se va a usar cuando se envíen correos electrónicos de notificación](media\change-subscriber-communication-preference.png)

    Si quiere agregar sus propias notas de referencia a la suscripción, puede hacerlo en la sección **Agregar referencia**.
    > [!div class="mx-imgBorder"]
    > ![Adición de notas de referencia propias a cada suscripción](media\add-subscriber-reference-notes.png) 

    Cuando haya terminado de seleccionar opciones y de especificar datos para el suscriptor, elija **Agregar** en la parte inferior de la ventana emergente **Agregar suscriptor**.
    > [!div class="mx-imgBorder"]
    > ![Elección del botón Agregar](media\add-button.png)

4. Después de agregar el suscriptor, se envía automáticamente un correo electrónico de asignación al nuevo suscriptor con más instrucciones. Puede volver a enviar el correo electrónico de asignación en cualquier momento si selecciona el suscriptor y hace clic en el botón **Reenviar** en el menú superior.
    > [!div class="mx-imgBorder"]
    > ![Reenvío del correo electrónico de activación a cualquier usuario o a varios usuarios siempre que se quiera](media\resend-subscriber-activation-emails.png) 

## <a name="bulk-assignments"></a>Asignaciones en masa

1. Para agregar varios suscriptores a la vez, vaya a la pestaña **Administrar suscriptores**. En la cinta de la parte superior, haga clic en **Agregar en masa**.
    > [!div class="mx-imgBorder"]
    > ![Adición de varios suscriptores](media\add-multiple-subscribers.png)

1. La asignación en masa usa una plantilla de Microsoft Excel para cargar los suscriptores. En el cuadro de diálogo para cargar varios suscriptores, haga clic en **Descargar** para descargar la plantilla.
    > [!div class="mx-imgBorder"]
    > ![Descarga de la plantilla de Excel para cargar varios suscriptores](media\download-template-upload-subscribers.png)

    > [!NOTE]
    > Descargue siempre la versión más reciente de esta plantilla. Si usa una versión antigua, se puede producir un error en la carga masiva.

1. En la hoja de cálculo de Excel, rellene los campos con la información de las personas a las que quiere asignar suscripciones. (El campo *Referencia* es opcional). Guarde el archivo localmente cuando haya terminado.

  Para garantizar una carga sin problemas, tenga en cuenta los siguientes procedimientos recomendados:

    - Asegúrese de que ninguno de los campos del formulario contiene comas.
    - Quite los espacios de delante y detrás de los campos del formulario.
    - Asegúrese de que los nombres de los usuarios no contienen espacios adicionales entre las dos partes de los nombres compuestos (por ejemplo, el nombre compuesto "Maggie May" se debe escribir como "MaggieMay", ya que el sistema no elimina el espacio adicional).

1. Vuelva al portal de administración de suscripciones de Visual Studio. En el cuadro de diálogo **Cargar varios suscriptores**, haga clic en **Examinar**.
    > [!div class="mx-imgBorder"]
    > ![Examen de la plantilla guardada para cargar varios suscriptores](media\bulk-add-browse-saved-template.png)

1. Vaya al archivo de Excel que ha guardado y haga clic en **Aceptar**.
    > [!div class="mx-imgBorder"]
    > ![Carga de la plantilla de Excel para cargar varios suscriptores](media\bulk-upload-subscribers.png)

    Aparece un cuadro de diálogo de progreso de carga.

    Si la plantilla contiene errores, se produce un error en la carga y se muestran los errores para que pueda corregir la plantilla e intentar de nuevo la carga en masa.
    > [!div class="mx-imgBorder"]
    > ![Mensaje de error si se produce un error en la carga de varios suscriptores](media\bulk-add-template-failed.png)

    Cuando la carga se realice correctamente, verá la lista de suscriptores y un mensaje de confirmación.
    > [!div class="mx-imgBorder"]
    > ![Mensaje de confirmación si la carga de varios suscriptores se realiza correctamente](media\bulk-add-template-success.png)
