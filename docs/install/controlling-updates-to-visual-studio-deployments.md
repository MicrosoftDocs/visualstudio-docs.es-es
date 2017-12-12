---
title: Control de actualizaciones a implementaciones de Visual Studio | Microsoft Docs
description: "{{MARCADOR DE POSICIÓN}}"
ms.date: 08/14/2017
ms.reviewer: tims
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: timsneath
ms.author: tglee
manager: ghogen
ms.openlocfilehash: f4e50777b8213a454942c0db710387bd7b59cde8
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2017
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Control de actualizaciones a implementaciones de Visual Studio basadas en red

Con frecuencia, los administradores de empresas crean un diseño y lo hospedan en un recurso compartido de red para implementarlo para sus usuarios finales.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Control de dónde Visual Studio busca actualizaciones
De manera predeterminada, Visual Studio continúa buscando actualizaciones en línea, incluso si la instalación se ha implementado desde un recurso compartido de red. Si hay alguna actualización disponible, el usuario puede instalarla. Cualquier contenido actualizado que no se encuentre en el diseño sin conexión se descarga de la web.

Si quiere control directo sobre el lugar donde Visual Studio busca actualizaciones, puede modificar la ubicación de búsqueda. También puede controlar la versión a la que se actualizan los usuarios. Para ello, siga estos pasos:

 1. Cree un diseño sin conexión:
    ```
    vs_enterprise.exe --layout C:\vs2017offline --lang en-US
    ```
 2. Cópielo en el recurso compartido de archivos donde desea hospedarlo:
    ```
    xcopy /e C:\vs2017offline \\server\share\VS2017
    ```
 3. Modifique el archivo response.json en el diseño y cambiar el valor `channelUri` para que apunte a una copia del archivo channelManifest.json que controla el administrador.

  Asegúrese de usar caracteres de escape de barra diagonal en el valor, como en el ejemplo siguiente:

  ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
  ```

 Ahora los usuarios finales pueden ejecutar la instalación de Visual Studio desde este recurso compartido.
    ```
    \\server\share\VS2017\vs_enterprise.exe
    ```

Cuando un administrador de empresa determina que es hora de que sus usuarios actualicen a una nueva versión de Visual Studio, pueden [actualizar la ubicación del diseño](update-a-network-installation-of-visual-studio.md) para incorporar los archivos actualizados, de la manera siguiente.

 1. Use un comando que sea similar al siguiente:
    ```
    vs_enterprise.exe --layout \\server\share\VS2017 --lang en-US
    ```
 2. Asegúrese de que el archivo response.json en el diseño actualizado todavía contenga sus personalizaciones, en concreto la modificación de channelUri, de la manera siguiente:
    ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
    ```
 Las instalaciones existentes de Visual Studio de este diseño buscan actualizaciones en `\\server\share\VS2017\ChannelManifest.json`. Si el archivo channelManifest.json es más reciente que el que ha instalado el usuario, Visual Studio notifica al usuario que hay una actualización disponible.

 Las nuevas instalaciones instalan automáticamente la versión actualizada de Visual Studio directamente desde el diseño.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Control de notificaciones en el IDE de Visual Studio
Como se ha descrito anteriormente, Visual Studio comprueba la ubicación desde la que se ha instalado, como un recurso compartido de red o Internet, para ver si hay actualizaciones disponibles. Cuando hay ninguna actualización disponible, Visual Studio avisa al usuario con una marca de notificación en la esquina superior derecha de la ventana.

 ![Notificación sobre las actualizaciones](media/notification-flag.png)

Si no quiere que a los usuarios finales se les notifiquen las actualizaciones, puede deshabilitar las notificaciones. Por ejemplo, puede que quiera deshabilitar las notificaciones si envía las actualizaciones mediante un mecanismo de distribución de software central.

Dado que Visual Studio 2017 [almacena las entradas del Registro en un registro privado](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), no puede modificar directamente el Registro de la manera normal. En cambio, Visual Studio incluye una utilidad `vsregedit.exe` que puede usar para cambiar la configuración de dicha aplicación. Puede desactivar las notificaciones con el siguiente comando:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```
Asegúrese de reemplazar el directorio para que coincida con la instancia instalada que quiera editar.

> [!TIP]
> Use [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) para buscar una instancia específica de Visual Studio en una estación de trabajo cliente.

## <a name="get-support"></a>Obtener soporte técnico
En ocasiones, algo no sale según lo previsto. Si se produce un error en la instalación de Visual Studio, consulte la página [Troubleshooting Visual Studio 2017 installation and upgrade issues](troubleshooting-installation-issues.md) (Solucionar problemas de errores de instalación y actualización de Visual Studio 2017). Si ninguno de los pasos de solución de problemas ayuda, puede ponerse en contacto con nosotros por chat para obtener asistencia para la instalación (solo en inglés). Para más información, consulte la [página de soporte técnico de Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Aquí tiene algunas opciones de soporte técnico más:
* Puede notificarnos problemas del producto a través de la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) que aparece en el instalador y en el IDE de Visual Studio.
* Puede compartir una sugerencia de producto con nosotros en [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Puede realizar el seguimiento de los problemas del producto en la [comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/), y hacer preguntas y encontrar respuestas.
* También puede ponerse en contacto con nosotros y otros desarrolladores de Visual Studio a través de nuestra [conversación de Visual Studio en la comunidad de Gitter](https://gitter.im/Microsoft/VisualStudio).  (Esta opción requiere una cuenta de [GitHub](https://github.com/)).

## <a name="see-also"></a>Vea también
* [Instalar Visual Studio](install-visual-studio.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Herramientas para administrar instancias de Visual Studio](tools-for-managing-visual-studio-instances.md)
