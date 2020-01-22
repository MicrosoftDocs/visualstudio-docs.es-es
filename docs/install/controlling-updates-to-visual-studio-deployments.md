---
title: Control de las actualizaciones de implementaciones
description: Obtenga información sobre cómo cambiar dónde busca Visual Studio una actualización cuando se instala desde una red.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 8743f042c7c33da34895f93e5df3990f6e0b2ed2
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115316"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Control de actualizaciones a implementaciones de Visual Studio basadas en red

Con frecuencia, los administradores de empresas crean un diseño y lo hospedan en un recurso compartido de red para implementarlo para sus usuarios finales.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Control de dónde Visual Studio busca actualizaciones

De manera predeterminada, Visual Studio continúa buscando actualizaciones en línea, incluso si la instalación se ha implementado desde un recurso compartido de red. Si hay alguna actualización disponible, el usuario puede instalarla. Cualquier contenido actualizado que no se encuentre en el diseño sin conexión se descarga de la web.

Si quiere control directo sobre el lugar donde Visual Studio busca actualizaciones, puede modificar la ubicación de búsqueda. También puede controlar la versión a la que se actualizan los usuarios. Para ello, siga estos pasos:

1. Cree un diseño sin conexión:

   ```cmd
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. Cópielo en el recurso compartido de archivos donde desea hospedarlo:

   ```cmd
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. Modifique el archivo response.json en el diseño y cambiar el valor `channelUri` para que apunte a una copia del archivo channelManifest.json que controla el administrador.

   Asegúrese de usar caracteres de escape de barra diagonal en el valor, como en el ejemplo siguiente:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Ahora los usuarios finales pueden ejecutar la instalación de Visual Studio desde este recurso compartido.

   ```cmd
   \\server\share\VS\vs_enterprise.exe
   ```

Cuando un administrador de empresa determina que es hora de que sus usuarios actualicen a una nueva versión de Visual Studio, pueden [actualizar la ubicación del diseño](update-a-network-installation-of-visual-studio.md) para incorporar los archivos actualizados, de la manera siguiente.

1. Use un comando que sea similar al siguiente:

   ```cmd
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. Asegúrese de que el archivo response.json en el diseño actualizado todavía contenga sus personalizaciones, en concreto la modificación de channelUri, de la manera siguiente:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Las instalaciones existentes de Visual Studio de este diseño buscan actualizaciones en `\\server\share\VS\ChannelManifest.json`. Si el archivo channelManifest.json es más reciente que el que ha instalado el usuario, Visual Studio notifica al usuario que hay una actualización disponible.

   Las nuevas instalaciones instalan automáticamente la versión actualizada de Visual Studio directamente desde el diseño.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Control de notificaciones en el IDE de Visual Studio

::: moniker range="vs-2017"

Como se ha descrito anteriormente, Visual Studio comprueba la ubicación desde la que se ha instalado, como un recurso compartido de red o Internet, para ver si hay actualizaciones disponibles. Cuando hay ninguna actualización disponible, Visual Studio avisa al usuario con una marca de notificación en la esquina superior derecha de la ventana.

   ![Notificación sobre las actualizaciones](media/notification-flag.png)

::: moniker-end

::: moniker range="vs-2019"

Como se ha descrito anteriormente, Visual Studio comprueba la ubicación desde la que se ha instalado, como un recurso compartido de red o Internet, para ver si hay actualizaciones disponibles. Cuando no hay ninguna actualización disponible, Visual Studio avisa al usuario con un icono de notificación en la esquina inferior derecha de la ventana.

   ![El icono de notificación en el IDE de Visual Studio](media/vs-2019/notification-bar.png "El icono de notificación en el IDE de Visual Studio")

::: moniker-end

Si no quiere que a los usuarios finales se les notifiquen las actualizaciones, puede deshabilitar las notificaciones. Por ejemplo, puede que quiera deshabilitar las notificaciones si envía las actualizaciones mediante un mecanismo de distribución de software central.

::: moniker range="vs-2017"

Dado que Visual Studio 2017 [almacena las entradas del Registro en un registro privado](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), no puede modificar directamente el Registro de la manera normal. En cambio, Visual Studio incluye una utilidad `vsregedit.exe` que puede usar para cambiar la configuración de dicha aplicación. Puede desactivar las notificaciones con el siguiente comando:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range="vs-2019"

Dado que Visual Studio 2019 [almacena las entradas del Registro en un registro privado](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), no se puede modificar directamente el Registro de la manera habitual. En cambio, Visual Studio incluye una utilidad `vsregedit.exe` que puede usar para cambiar la configuración de dicha aplicación. Puede desactivar las notificaciones con el siguiente comando:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

Asegúrese de reemplazar el directorio para que coincida con la instancia instalada que quiera editar.

> [!TIP]
> Use [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) para buscar una instancia específica de Visual Studio en una estación de trabajo cliente.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Instalar Visual Studio](install-visual-studio.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Herramientas para administrar instancias de Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Ciclo de vida y mantenimiento del producto de Visual Studio](/visualstudio/releases/2019/servicing/)
