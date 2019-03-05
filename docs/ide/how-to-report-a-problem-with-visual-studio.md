---
title: Cómo notificar un problema con Visual Studio
titleSuffix: ''
description: Obtenga información sobre cómo notificar un problema con Visual Studio a Microsoft, para que podamos diagnosticarlo y corregirlo.
ms.date: 03/11/2018
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76571106832c79ea3ecc7aa6d1b2e58355912960
ms.sourcegitcommit: 1c8e07b98fc0a44b5ab90bcef77d9fac7b3eb452
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/25/2019
ms.locfileid: "56800696"
---
# <a name="how-to-report-a-problem-with-visual-studio"></a>Cómo notificar un problema con Visual Studio

Si experimenta un problema con Visual Studio, nos gustaría que nos lo comunicara. Aquí le mostramos cómo notificar un problema a la [Comunidad de desarrolladores](https://developercommunity.visualstudio.com/) para que podamos diagnosticarlo y corregirlo.

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Cómo notificar un problema en Visual Studio para Mac](/visualstudio/mac/report-a-problem).

## <a name="report-a-problem-by-using-visual-studio"></a>Notificación de un problema con Visual Studio

Para notificar un problema de Visual Studio, debe iniciar el informe en Visual Studio o el instalador de Visual Studio. No podrá hacerlo directamente a través del sitio web de la [Comunidad de desarrolladores](https://developercommunity.visualstudio.com/). La generación de informes mediante Visual Studio permite incluir información de diagnóstico automáticamente en el informe.

![Menú emergente para notificar un problema en la Comunidad de desarrolladores de Visual Studio](media/report-an-issue.png)

1. En Visual Studio, seleccione **Ayuda** > **Enviar comentarios** > **Notificar un problema**.

   > [!TIP]
   > Si no puede completar la instalación de Visual Studio o no puede tener acceso a la herramienta de comentarios dentro de Visual Studio, puede notificar un problema mediante el **Instalador de Visual Studio**. Para ello, haga clic en el icono de comentario en la esquina superior derecha del **Instalador de Visual Studio**.

1. Si no ha iniciado sesión, seleccione **Iniciar sesión**; se encuentra en la parte derecha de la herramienta, tal y como se muestra en la siguiente captura de pantalla. Siga las instrucciones en pantalla para iniciar sesión.

   ![Inicie sesión para notificar un problema](../ide/media/sign-in-new-ux.png)

   Para notificar un problema que esté experimentando, inicie sesión. También puede votar por otros problemas publicados o agregar comentarios.

1. Cuando haya iniciado sesión, podrá ver sus **Problemas** y **Actividad** en la pantalla **Elementos que sigo**.

    ![Elementos que sigo](../ide/media/items-i-follow.png)

1. Visual Studio proporciona una interfaz que permite buscar el problema y ver si otros usuarios lo han notificado. Si alguien lo ha notificado, "vótelo" para indicárnoslo.
   > [!NOTE]
   > Para realizar una búsqueda, indique el texto en el cuadro de búsqueda y presione Entrar o haga clic en el icono de búsqueda.

   ![Buscar y votar problemas similares](../ide/media/search-and-vote.png)

1. Si no encuentra el problema que ha detectado, elija **Informar de un problema nuevo** en la parte inferior de la pantalla.

   > [!NOTE]
   > El botón **Informar de un problema nuevo** solo aparece en la interfaz de Visual Studio correspondiente a la Comunidad de desarrolladores. No se puede notificar un problema directamente en el sitio web de la [Comunidad de desarrolladores](https://developercommunity.visualstudio.com/).

1. Asigne un título descriptivo al problema que nos ayude a dirigirlo al equipo de Visual Studio correcto.

1. Proporcione detalles adicionales y, si es posible, los pasos para reproducir el problema.

   ![Notificar un problema nuevo](../ide/media/report-new-problem.png)

1. Seleccione **Siguiente** para ir a la pestaña **Datos adjuntos**. Aquí puede hacer una captura de la pantalla actual para enviársela a Microsoft. Para adjuntar capturas de pantalla adicionales u otros archivos, elija **Adjuntar archivos adicionales**.

   ![Adjuntar una captura de pantalla a un informe de problemas de Visual Studio](media/report-a-problem-screenshot.png)

1. Si no quiere adjuntar una captura de pantalla ni [grabar una reproducción](#record-a-repro), seleccione **Siguiente** para ir a la pestaña **Resumen**.

1. Seleccione **Enviar** para enviar el informe junto con todas las imágenes y archivos de volcado o de seguimiento. (Si el botón **Enviar** está atenuado, asegúrese de que ha proporcionado un título y una descripción para el informe).

   Para obtener información sobre qué datos se recopilan, vea [Datos que recopilamos](developer-community-privacy.md#data-we-collect).

## <a name="record-a-repro"></a>Grabación de una reproducción

Los archivos de seguimiento y de volcado de memoria del montón nos ayudan a diagnosticar problemas. Apreciamos mucho que use la herramienta **Notificar un problema** para grabar los pasos de reproducción y enviar los datos a Microsoft. A continuación le mostramos cómo hacerlo:

1. Tras escribir un título y una descripción del problema, seleccione **Siguiente** para ir a la pestaña **Datos adjuntos**.

1. Haga clic en la pestaña **Grabar**.

1. Si puede reproducir el problema en Visual Studio, seleccione la instancia actual en **Grabar sus acciones**. Si no puede, por ejemplo, en el caso de que Visual Studio esté bloqueado, seleccione **\<Crear una instancia nueva>** para grabar las acciones en una instancia nueva de Visual Studio.

1. Seleccione **Iniciar grabación**. Proporcione permiso para ejecutar la herramienta.

   ![Elija "Iniciar grabación" para proporcionar un archivo de seguimiento y de volcado de memoria del montón en un informe de problema de Visual Studio.](../ide/media/record-dialog-box.png)

1. Cuando aparezca la herramienta **Grabación de acciones de usuario**, realice los pasos que reproducen el problema.

1. Cuando haya terminado, haga clic en el botón **Detener grabación**.

1. Espere unos minutos mientras Visual Studio recopila y empaqueta la información que ha grabado.

   Para obtener información sobre qué datos se recopilan, vea [Datos que recopilamos](developer-community-privacy.md#data-we-collect).

## <a name="when-further-information-is-needed-need-more-info"></a>En caso de necesitar más información (Se necesita más información)

A partir de la versión 15.5 de Visual Studio 2017, hay un nuevo flujo de trabajo para ayudar a los usuarios a proporcionar información adicional en los informes de problemas.

1. Si un ingeniero de Microsoft establece el problema de la [Comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/) en el estado **Se necesita más información**, los usuarios que hayan publicado, votado, seguido o comentado el problema recibirán una notificación en la herramienta **Notificar un problema** de Visual Studio.

   ![Notificación Se necesita más información en Visual Studio](../ide/media/nmi-notification.png)

1. Haga clic en el vínculo **Ver problemas** para filtrar y ordenar la vista por los problemas que requieran atención. Estos problemas también tienen un indicador junto a ellos, para diferenciarlos en la búsqueda en general.

1. Haga clic en un problema para ver sus detalles.

   ![Notificación Se necesita más información](../ide/media/nmi-details-view.png)

1. Para ver la solicitud **Se necesita más información**, haga clic en el vínculo **Ver la solicitud y responder** de la vista de detalles del problema. Cuadro de diálogo en el que se muestra la solicitud.

   ![Notificación Se necesita más información](../ide/media/nmi-request.png)

1. Para proporcionar más información, puede agregar comentarios, datos adjuntos o grabar los pasos. Esta experiencia es similar a la notificación de un nuevo problema o a la de proporcionar información adicional cuando se vota un problema.

1. El ingeniero de Microsoft que haya solicitado la información recibirá una notificación cuando se agregue información adicional. Si tienen información suficiente para investigar el problema, cambiarán el estado. En caso contrario, el ingeniero solicitará más información.

   > [!NOTE]
   > * Cuando responda, la notificación desaparecerá. En su lugar, verá un banner en el que se le dan las gracias y se le indica un método para proporcionar más información.
   > * Cuando el estado del problema cambie, la notificación desaparecerá para todos los usuarios que sigan el problema.
   > * A una misma solicitud **Se necesita más información** pueden responder varias personas.
   > * Al acceder a la [Comunidad de desarrolladores](https://developercommunity.visualstudio.com/) directamente mediante un explorador web, no aparece no hay ningún flujo de trabajo **Se necesita más información**, pero sí que puede proporcionar comentarios y datos adjuntos mediante ese método.

## <a name="search-for-solutions-or-provide-feedback"></a>Búsqueda de soluciones o envío de comentarios

Si no quiere o no puede notificar un problema mediante Visual Studio, es posible que ese problema ya se haya notificado y que se haya publicado una solución en la página [Comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/).

Si no tiene ningún problema que notificar pero quiere sugerir una característica, también hay un lugar para eso. Para obtener más información, vea la página [Sugerir una característica](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).

## <a name="see-also"></a>Vea también

* [Hable con nosotros](../ide/talk-to-us.md)
* [Notificación de un problema con Visual Studio para Mac](/visualstudio/mac/report-a-problem)
* [Notificación de un problema con C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/)
* [Privacidad de datos de la Comunidad de desarrolladores](developer-community-privacy.md)