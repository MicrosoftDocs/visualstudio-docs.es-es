---
title: Control de las actualizaciones de implementaciones
description: Obtenga información sobre cómo cambiar dónde busca Visual Studio una actualización cuando se instala desde una red.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 8360c48e9868f6ed5d81fffc748d050404211228
ms.sourcegitcommit: 56060e3186086541d9016d4185e6f1bf3471e958
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/07/2021
ms.locfileid: "106547497"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Control de actualizaciones a implementaciones de Visual Studio basadas en red

Con frecuencia, los administradores de empresas crean un diseño y lo hospedan en un recurso compartido de red para implementarlo en sus usuarios finales. En esta página se describe cómo configurar las opciones de diseño de red correctamente. 

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Control de dónde Visual Studio busca actualizaciones

**Escenario 1: El cliente se instaló originalmente desde un diseño, pero está configurado para recibir actualizaciones de la ubicación de diseño de red o de la web**

De manera predeterminada, Visual Studio continúa buscando actualizaciones en línea, incluso si la instalación se ha implementado originalmente desde un recurso compartido de red. Si hay alguna actualización disponible en la web, el usuario puede instalarla. Aunque la caché de diseño de red se inspecciona primero para buscar los bits de producto actualizados, si no se encuentran allí, Visual Studio buscará y descargará los bits de producto actualizados desde la web.

**Escenario 2: El cliente se instaló originalmente y solo debe recibir actualizaciones del diseño de red**

Si quiere controlar dónde busca actualizaciones el cliente de Visual Studio, por ejemplo, cuando la máquina cliente no tiene acceso a Internet, y quiere asegurarse de que solo y siempre se instale desde el diseño, puede configurar la ubicación donde el instalador del cliente buscará los bits de producto actualizados. Antes de que el cliente realice la instalación inicial desde el diseño, es mejor asegurarse de que esta opción está configurada correctamente. 

1. Cree un diseño sin conexión:

   ```cmd
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. Cópielo en el recurso compartido de archivos donde desea hospedarlo:

   ```cmd
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. Modifique el archivo `response.json` del diseño y cambie el valor de `channelUri` para que apunte a una copia del archivo channelManifest.json que controla el administrador.

   Asegúrese de usar caracteres de escape de barra diagonal en el valor, como en el ejemplo siguiente:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Ahora los usuarios finales pueden ejecutar la instalación de Visual Studio desde este recurso compartido.

   ```cmd
   \\server\share\VS\vs_enterprise.exe
   ```

Cuando un administrador de empresa determina que es hora de que sus usuarios actualicen a una nueva versión de Visual Studio, pueden [actualizar la ubicación del diseño](update-a-network-installation-of-visual-studio.md) para incorporar los archivos actualizados, de la manera siguiente.

1. Use un comando que sea similar al siguiente:

   ```cmd
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. Asegúrese de que el archivo `response.json` del diseño actualizado todavía contenga sus personalizaciones, en concreto, la modificación de channelUri, de la manera siguiente:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

Las instalaciones existentes de Visual Studio de este diseño buscan actualizaciones en `\\server\share\VS\ChannelManifest.json`. Si el archivo channelManifest.json es más reciente que el que ha instalado el usuario, Visual Studio notifica al usuario que hay una actualización disponible.

Cualquier actualización de la instalación iniciada desde el cliente instalará automáticamente la versión actualizada de Visual Studio directamente desde el diseño.

**Escenario 3: El cliente se instaló originalmente desde la web, pero ahora solo debería recibir actualizaciones de un diseño de red**

En algunos casos, es posible que la máquina cliente ya haya instalado Visual Studio desde la web, pero ahora el administrador quiere que todas las actualizaciones futuras provengan de un diseño administrado. La única manera admitida de hacerlo es crear un diseño de red con la versión deseada del producto y, luego, ejecutar el programa previo en la máquina cliente _desde la ubicación de diseño_ (por ejemplo, `\\network\share\vs_enterprise.exe`). Lo ideal es que la instalación del cliente original haya sucedido usando el programa previo desde el diseño de red con el valor de ChannelURI configurado correctamente, pero la ejecución del programa previo actualizado desde la ubicación del diseño de red también funcionará. Cualquiera de estas acciones insertaría en la máquina cliente una conexión con esa ubicación de diseño concreta. La único que hay que tener en cuenta para que este escenario funcione correctamente es que el valor de "ChannelURI" en el archivo `response.json` del diseño sea el mismo que el que se estableció en la máquina del cliente cuando se produjo la instalación original. Lo más probable es que este valor se haya establecido originalmente en el [canal de versiones](https://aka.ms/vs/16/release/channel) de Internet. 


## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Control de notificaciones en el IDE de Visual Studio

::: moniker range="vs-2017"

Como se ha descrito anteriormente, Visual Studio comprueba la ubicación desde la que se ha instalado, como un recurso compartido de red o Internet, para ver si hay actualizaciones disponibles. Cuando hay ninguna actualización disponible, Visual Studio avisa al usuario con una marca de notificación en la esquina superior derecha de la ventana.

   ![Notificación sobre las actualizaciones](media/notification-flag.png)

::: moniker-end

::: moniker range="vs-2019&quot;

Como se ha descrito anteriormente, Visual Studio comprueba la ubicación desde la que se ha instalado, como un recurso compartido de red o Internet, para ver si hay actualizaciones disponibles. Cuando no hay ninguna actualización disponible, Visual Studio avisa al usuario con un icono de notificación en la esquina inferior derecha de la ventana.

   ![El icono de notificación en el IDE de Visual Studio](media/vs-2019/notification-bar.png &quot;El icono de notificación en el IDE de Visual Studio")

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

* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Habilitación de las actualizaciones de administrador](enabling-administrator-updates.md)
* [Aplicación de las actualizaciones de administrador](applying-administrator-updates.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Herramientas para administrar instancias de Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Ciclo de vida y mantenimiento del producto de Visual Studio](/visualstudio/releases/2019/servicing/)
