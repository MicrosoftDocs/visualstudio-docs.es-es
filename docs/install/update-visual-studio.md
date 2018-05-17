---
title: Actualizar Visual Studio 2017
description: Obtenga información sobre cómo actualizar Visual Studio a la versión más reciente, paso a paso.
ms.date: 04/23/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- update Visual Studio
- change visual studio
- changing Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c0a53ca3a5b7eb292a2b2bdd1e95b9319205bcf3
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="update-visual-studio-2017-to-the-most-recent-release"></a>Actualizar Visual Studio 2017 a la versión más reciente

Le recomendamos que actualice a la [versión más reciente](/visualstudio/releasenotes/vs2017-relnotes) de Visual Studio 2017 para recibir siempre las características, correcciones y mejoras más recientes.

Y si desea probar algo antes de que lo publiquemos, piense en descargar también la [versión preliminar](/visualstudio/releasenotes/vs2017-preview-relnotes) de la siguiente versión.

> [!IMPORTANT]
> Para instalar, actualizar o modificar Visual Studio, debe iniciar sesión con una cuenta que tenga permisos administrativos. Para obtener más información, vea [Permisos de usuario y Visual Studio](../ide/user-permissions-and-visual-studio.md).

## <a name="update-visual-studio-2017-version-156-or-later"></a>Actualización de Visual Studio 2017, versión 15.6 o posterior

Se ha simplificado la experiencia de instalación y actualización para que resulte más fácil de usar directamente desde el IDE. Aquí se muestra cómo actualizar desde la versión 15.6 y versiones posteriores a versiones más recientes de Visual Studio.

### <a name="use-the-notifications-hub"></a>Uso del Centro de notificaciones

Cuando haya una actualización, aparecerá la correspondiente marca de notificaciones en Visual Studio.

1. No olvide guardar su trabajo.

2. Haga clic en la marca de notificaciones para abrir el Centro de **notificaciones** y, después, elija la actualización que desea instalar.

  ![Actualizar Visual Studio 2017 mediante el Centro de Notificaciones](media/vs-install-notifications-hub-15dot6.png "El Centro de notificaciones en Visual Studio 2017")

3. Cuando aparezca el cuadro de diálogo **Actualizar**, elija **Actualizar ahora**.

    ![Actualizar Visual Studio 2017 mediante el Centro de notificaciones](media/vs-update-now-from-notifications-hub.png "Cuadro de diálogo Actualizar en el Centro de notificaciones de Visual Studio")

     Si se abre un cuadro de diálogo de Control de acceso de usuario, elija **Sí**. Es posible que aparezca el cuadro de diálogo "Espere" durante un momento, y luego el instalador de Visual Studio se abre para iniciar la actualización.

     ![La nueva experiencia del instalador de Visual Studio en la versión 15.6](media/visual-studio-15dot6-installer.png "The new Visual Studio Installer experience in version 15.6")

     La actualización continúa. Cuando se haya completado, Visual Studio se reiniciará.

     > [!NOTE]
     > Al ejecutar Visual Studio en modo de administrador, debe reiniciar Visual Studio manualmente después de la actualización.

### <a name="use-the-ide"></a>Uso del IDE

Puede buscar una actualización y, a continuación, instalarla desde la barra de menús de Visual Studio.

1. No olvide guardar su trabajo.

2. Elija **Ayuda** > **Buscar actualizaciones**.

     ![El nuevo menú Ayuda de Visual Studio, versión 15.6](media/vs-help-menu-check-for-updates.png "The new Help menu in Visual Studio version 15.6")

3. Cuando aparezca el cuadro de diálogo **Actualizar**, elija **Actualizar ahora**.

   La actualización continúa como se describe en la sección anterior y Visual Studio se reinicia una vez que la actualización finalice correctamente.

   > [!NOTE]
   > Al ejecutar Visual Studio en modo de administrador, debe reiniciar Visual Studio manualmente después de la actualización.

### <a name="use-the-visual-studio-installer"></a>Uso del instalador de Visual Studio

Al igual que en versiones anteriores de Visual Studio de 2017, puede usar el instalador de Visual Studio para instalar una actualización.

1. No olvide guardar su trabajo.

2. Abra el instalador. El instalador de Visual Studio podría necesitar una actualización antes de continuar.

  > [!NOTE]
  > En un equipo con Windows 10, encontrará el instalador en la letra **I**, como **Instalador de Visual Studio**, o en la letra **M**, como **Microsoft Visual Studio Installer** (Instalador de Microsoft Visual Studio).

2. En la página **Producto** del instalador, busque la edición de Visual Studio que tenga instalada.

3. Si hay alguna actualización disponible, verá el botón **Actualizar**. (El instalador podría tardar unos segundos en determinar si hay alguna actualización disponible).

  Haga clic en el botón **Actualizar** para instalar las actualizaciones.

     ![Actualizar Visual Studio 2017 mediante el instalador de Visual Studio](media/update-visual-studio.png "Actualizar Visual Studio 2017 mediante el instalador de Visual Studio")

## <a name="update-visual-studio-2017-version-155-or-earlier"></a>Actualización de Visual Studio 2017, versión 15.5 o anteriores

Si está utilizando una versión anterior, aquí se muestra cómo aplicar una actualización a las versiones de Visual Studio 2017 entre 15.0 y 15.5.

### <a name="update-by-using-the-notifications-hub"></a>Actualizar mediante el centro de Notificaciones

1. Cuando haya actualizaciones, aparecerá la correspondiente marca de notificaciones en Visual Studio.

  ![Actualizar Visual Studio 2017 mediante la Central de notificaciones](media/notification-flag.png "Marca de notificación de actualización en Visual Studio")

  Haga clic en la marca de notificación para abrir la Central de **notificaciones**.

  ![Actualizar Visual Studio 2017 mediante el centro de Notificaciones](media/notifications-hub.png "Centro de Notificaciones en Visual Studio")

2. Haga clic en **Está disponible la actualización de Visual Studio** para abrir el cuadro de diálogo **Extensiones y actualizaciones**.

  ![Actualizar Visual Studio 2017 mediante el Hub de notificaciones](media/notifications-hub-select.png "Hub de notificaciones en Visual Studio")

3. En el cuadro de diálogo **Extensiones y actualizaciones**, haga clic en el botón **Actualizar**.

  ![Actualizar Visual Studio 2017 mediante el Hub de notificaciones](media/notifications-extensions-and-updates.png "Cuadro de diálogo Extensiones y actualizaciones en Visual Studio")

#### <a name="more-about-visual-studio-notifications"></a>Más información sobre las notificaciones de Visual Studio

Visual Studio le avisa cuando una actualización está disponible para Visual Studio o cualquier componente, y también cuando se producen determinados eventos en el entorno de Visual Studio.

* Cuando la marca de notificación es de color amarillo, hay una actualización de producto de Visual Studio disponible para instalar.
* Cuando la marca de notificación es de color rojo, hay un problema con la licencia.
* Cuando la marca de notificación es de color negro, hay mensajes opcionales o informativos para revisar.

Haga clic en la marca de notificaciones para abrir la Central de **notificaciones** y, después, elija las notificaciones sobre las que quiere actuar. O bien, puede optar por omitir o descartar una notificación.

 ![Ver un mensaje informativo u opcional en la Central de notificaciones](media/notification-flag-optional.png "La marca de notificación de mensaje opcional o informativo en Visual Studio")

Si elige ignorar una notificación, Visual Studio deja de mostrarla. Si quiere restablecer la lista de notificaciones omitidas, seleccione el botón **Configuración** en el Centro de notificaciones.

   ![Hacer clic en el botón Configuración en la Central de notificaciones para ver las opciones de notificación](media/vs-notifications-hub-settings-button.png "Hacer clic en el botón Configuración en la Central de notificaciones para ver las opciones de notificación")

### <a name="update-by-using-the-visual-studio-installer"></a>Actualizar mediante el instalador de Visual Studio

1. Abra el instalador. Es posible que deba actualizar el instalador antes de continuar. Si es así, se le pedirá que lo haga.

  > [!NOTE]
  > En un equipo con Windows 10, encontrará el instalador en la letra **I**, como **Instalador de Visual Studio**, o en la letra **M**, como **Microsoft Visual Studio Installer** (Instalador de Microsoft Visual Studio).

2. En la página **Producto** del instalador, busque la edición de Visual Studio que tenga instalada.

3. Si hay alguna actualización disponible, verá el botón **Actualizar**. (El instalador podría tardar unos segundos en determinar si hay alguna actualización disponible).

  Haga clic en el botón **Actualizar** para instalar las actualizaciones.

     ![Actualizar Visual Studio 2017 mediante el instalador de Visual Studio](media/update-visual-studio.png "Actualizar Visual Studio 2017 mediante el instalador de Visual Studio")

## <a name="get-support"></a>Obtener soporte técnico

En ocasiones, algo no sale según lo previsto. Si se produce un error en la instalación de Visual Studio, consulte la página [Troubleshooting Visual Studio 2017 installation and upgrade issues](troubleshooting-installation-issues.md) (Solucionar problemas de errores de instalación y actualización de Visual Studio 2017). Si ninguno de los pasos de solución de problemas ayuda, puede ponerse en contacto con nosotros por chat para obtener asistencia para la instalación (solo en inglés). Para más información, consulte la [página de soporte técnico de Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Aquí tiene algunas opciones de soporte técnico más:

* Puede notificarnos problemas del producto a través de la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) que aparece en el instalador y en el IDE de Visual Studio.
* Puede compartir una sugerencia de producto con nosotros en [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Puede realizar el seguimiento de los problemas del producto y encontrar respuestas en la [comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/).
* También puede ponerse en contacto con nosotros y otros desarrolladores de Visual Studio a través de la [conversación de Visual Studio en la comunidad de Gitter](https://gitter.im/Microsoft/VisualStudio). (Esta opción requiere una cuenta de [GitHub](https://github.com/)).

## <a name="see-also"></a>Vea también

* [Instalación de Visual Studio 2017](install-visual-studio.md)
* [Modificación de Visual Studio 2017](modify-visual-studio.md)
* [Desinstalación de Visual Studio 2017](uninstall-visual-studio.md)
* [Guía de administradores de Visual Studio](visual-studio-administrator-guide.md)
