---
title: Cómo notificar un problema con Visual Studio
description: Obtenga información sobre cómo notificar un problema con Visual Studio.
ms.date: 03/11/2018
ms.topic: how-to
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2956372882d4449345d026e691a12afb2988054a
ms.sourcegitcommit: 6ef4e46c786c5bbcc52cd9c30e5ddfca12ea8b3c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "97050837"
---
# <a name="how-to-report-a-problem-with-visual-studio-or-visual-studio-installer"></a>Cómo notificar un problema con Visual Studio o con el Instalador de Visual Studio

> [!NOTE]
> En el caso de Visual Studio para Mac, vea [Cómo notificar un problema en Visual Studio para Mac](/visualstudio/mac/report-a-problem).

Puede notificar un problema desde Visual Studio o desde su instalador. Con la herramienta de comentarios integrada es más fácil agregar información de diagnóstico, que los equipos de Visual Studio pueden usar para diagnosticar problemas y corregirlos. Estos son los pasos necesarios para notificar un problema.

1. **En Visual Studio**, seleccione el icono de comentarios en la esquina superior derecha y seleccione Notificar un problema. También puede acceder a la Herramienta para enviar comentarios desde el menú **Ayuda** > **Enviar comentarios** > **Notificar un problema**.
![Ventana emergente Notificar un problema en la Comunidad de desarrolladores de Visual Studio](media/feedback-button.png) Como alternativa, notifique un problema en el **Instalador de Visual Studio** si no puede instalar Visual Studio o si no puede acceder a la Herramienta para enviar comentarios en Visual Studio.  En el instalador, seleccione el icono de comentarios en la esquina superior derecha y seleccione Notificar un problema.
![Menú emergente para notificar un problema en la Comunidad de desarrolladores de Visual Studio](media/installer.png)

1. Al hacer clic en **Notificar un problema**, se abre el explorador predeterminado y se inicia sesión con la misma cuenta con la que inicia sesión en Visual Studio.

   ![Inicie sesión para notificar un problema](../ide/media/feedback-browser-top.png)

1. Empiece por escribir el título descriptivo del informe de errores. Debe tener al menos 25 caracteres de longitud.

    ![Notificar un problema](../ide/media/feedback-report.png)

1. Cuando empiece a escribir, se mostrarán los posibles duplicados en el campo de título.

    ![Buscar duplicados](../ide/media/feedback-search.png)

1. Seleccione los posibles informes de errores de duplicados para ver si hay uno que coincida con su problema. Si es así, vote por él en lugar de crear su propio vale.

    ![Votar duplicados](../ide/media/feedback-duplicate.png)

2. Si no se ha encontrado ningún duplicado, escriba una descripción del problema para continuar. Es importante ser lo más claro posible para aumentar las posibilidades de que podamos reproducir el error. Asegúrese de incluir pasos claros de reproducción.

3. Si es relevante para el informe de errores, active la casilla *Incluir captura de pantalla* de Visual Studio para crear una captura de pantalla.

    ![Realice una captura de pantalla](../ide/media/feedback-screenshot.png) *Solo los ingenieros de Microsoft pueden ver la captura de pantalla*

    Puede incluso recortar la captura de pantalla directamente en el explorador para quitar cualquier elemento que sea confidencial o no esté relacionado.

4. Una de las mejores formas de ayudar al equipo de ingeniería de Visual Studio a resolver el problema es proporcionar un seguimiento y archivos de volcado de memoria del montón para que los examinen. Una manera fácil de hacerlo es grabar los pasos que han provocado el error.

    ![Grabe sus acciones](../ide/media/feedback-recording.png) *Solo los ingenieros de Microsoft pueden ver la grabación*

5. Revise los archivos adjuntos y cargue archivos adicionales si cree que servirá para diagnosticar el problema.

    ![Archivos adjuntos](../ide/media/feedback-attachments.png) *Solo los ingenieros de Microsoft pueden ver los archivos adjuntos*

6. El último paso consiste en pulsar el botón **Enviar**. Al enviar el informe, se enviará directamente al sistema interno de informes de errores de Visual Studio a la espera de la evaluación del error.

## <a name="when-further-information-is-needed"></a>Cuando se necesita más información

En el caso de que a una incidencia le falte información importante, le asignaremos el estado pertinente para indicar que **se requiere más información**. Agregaremos un comentario en la incidencia con la información específica que necesitamos y recibirá una notificación por correo electrónico. Si no recibimos la información en un plazo de siete días, le enviaremos un recordatorio. Tras ese recordatorio, cerraremos la solicitud después de 14 días de inactividad.

1. Siga el vínculo del correo electrónico al informe de problemas o vaya a la página principal para ver todos los informes en el estado **Necesita más información**.

    ![Mis comentarios](../ide/media/feedback-my-feedback.png)

1. Al seleccionar el vínculo Proporcionar más información del informe de problemas, se muestra una nueva pantalla. Desde aquí, puede ver qué información se solicita.

   ![Mis comentarios](../ide/media/feedback-need-more-info.png)

1. Para proporcionar más información, puede agregar comentarios, datos adjuntos o grabar los pasos. Esta experiencia es similar a la notificación de un nuevo problema o a la de proporcionar información adicional cuando se vota un problema.

1. El ingeniero de Microsoft que haya solicitado la información recibirá una notificación cuando se agregue información adicional. Si tienen información suficiente para investigar el problema, cambiarán el estado. En caso contrario, el ingeniero solicitará más información.

Puede ver estas solicitudes en la pantalla **Mis comentarios** junto con los demás **Problemas** y **Sugerencias**.

## <a name="search-for-solutions-or-provide-feedback"></a>Búsqueda de soluciones o envío de comentarios

Si no quiere o no puede notificar un problema mediante Visual Studio, es posible que ese problema ya se haya notificado y que se haya publicado una solución en la página [Comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/).

Si no tiene ningún problema que notificar, pero quiere sugerir una característica, también hay un lugar para hacerlo. Para obtener más información, vea la página [Sugerir una característica](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).

## <a name="see-also"></a>Vea también

* [Guía sobre la Comunidad de desarrolladores](./developer-community-guidelines.md)
* [Opciones de comentarios de Visual Studio](../ide/feedback-options.md)
* [Notificación de un problema con Visual Studio para Mac](/visualstudio/mac/report-a-problem)
* [Notificación de un problema con C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/)
* [Privacidad de datos de la Comunidad de desarrolladores](developer-community-privacy.md)