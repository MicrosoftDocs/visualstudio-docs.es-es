---
title: Creación de una instalación sin conexión
description: Obtenga información sobre cómo instalar Visual Studio sin conexión cuando la conexión a internet no sea de confianza o disponga de poco ancho de banda.
ms.date: 07/24/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 616c27f16b4fca9be6f8dab3cdf70fafae52f193
ms.sourcegitcommit: 0f5f7955076238742f2071d286ad8e896f3a6cad
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/25/2019
ms.locfileid: "68483506"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Crear una instalación sin conexión de Visual Studio

::: moniker range="vs-2017"

Hemos diseñado Visual Studio 2017 para que funcione bien en una variedad de configuraciones de red y de equipos. Aunque se recomienda que pruebe el [instalador web de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) &mdash;que es un archivo pequeño y le permite estar actualizado con todas las correcciones y características más recientes&mdash; somos conscientes de que es posible que no pueda hacerlo.

::: moniker-end

::: moniker range="vs-2019"

Hemos diseñado Visual Studio 2019 para que funcione bien en una variedad de configuraciones de red y de equipos. Aunque se recomienda que pruebe el [instalador web de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) &mdash;que es un archivo pequeño y le permite estar actualizado con todas las correcciones y características más recientes&mdash; somos conscientes de que es posible que no pueda hacerlo.

::: moniker-end

Por ejemplo, puede que disponga de una conexión a Internet no confiable o de poco ancho de banda. En ese caso, dispone de varias opciones: puede usar la nueva característica "Download all, then install" (Descargar todo y volver a instalar) para descargar los archivos antes de instalar, o puede usar la línea de comandos para crear una caché local de los archivos.

> [!NOTE]
> Si es un administrador de empresa que quiere realizar una implementación de Visual Studio en una red de estaciones de trabajo del cliente con firewall desde Internet, vea las páginas [Creación de una instalación de red de Visual Studio](../install/create-a-network-installation-of-visual-studio.md) e [Instalar los certificados necesarios para la instalación sin conexión de Visual Studio](../install/install-certificates-for-visual-studio-offline.md).

## <a name="use-the-download-all-then-install-feature"></a>Usar la característica "Download all, then install" (Descargar todo y volver a instalar)

::: moniker range="vs-2017"

[**Novedades de la versión 15.8**](/visualstudio/releasenotes/vs2017-relnotes-v15.8#install): después de descargar el instalador web, seleccione la nueva opción **"Download all, then install"** (Descargar todo y volver a instalar) en el instalador de Visual Studio. Después, continúe con la instalación.

   ![Opción "Download all, then install" (Descargar todo y volver a instalar)](media/download-all-then-install.png)

::: moniker-end

::: moniker range="vs-2019"

después de descargar el instalador web, seleccione la nueva opción **"Download all, then install"** (Descargar todo y volver a instalar) en el instalador de Visual Studio. Después, continúe con la instalación.

   ![Opción "Download all, then install" (Descargar todo y volver a instalar)](media/vs-2019/download-all-then-install-from-installer.png)

::: moniker-end

Hemos diseñado la característica de descargar todo y volver a instalar para que pueda descargar Visual Studio como una única instalación para el mismo equipo en el que lo descargó. De esta forma, puede desconectarse de la web de forma segura antes de instalar Visual Studio.

> [!IMPORTANT]
> No utilice la característica de descargar todo y volver a instalar para crear una caché sin conexión que desee transferir a otro equipo. No se ha diseñado para trabajar de este modo. <br><br>Si quiere crear una caché sin conexión para instalar Visual Studio en otro equipo, vea la sección [Usar la línea de comandos para crear una memoria caché local](#use-the-command-line-to-create-a-local-cache) de esta página para obtener información sobre cómo crear una caché local, o la página [Creación de una instalación de red de Visual Studio](../install/create-a-network-installation-of-visual-studio.md) para obtener información sobre cómo crear una caché de red.

## <a name="use-the-command-line-to-create-a-local-cache"></a>Usar la línea de comandos para crear una memoria caché local

Después de descargar un pequeño programa previo, use la línea de comandos para crear una memoria caché local. Después, use la memoria caché local para instalar Visual Studio. (Este proceso reemplaza los archivos ISO que había disponibles para las versiones anteriores).

Esta es la manera de hacerlo.

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>Paso 1: Descargar el programa previo de Visual Studio

Deberá disponer de conexión a Internet para poder completar este paso.

Para comenzar, descargue el programa previo de Visual Studio para la edición elegida de Visual Studio. El archivo de instalación &mdash;o programa previo&mdash; corresponderá o será parecido a uno de los siguientes.

::: moniker range="vs-2017"

| Edition                    | Archivo                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Comunidad de Visual Studio    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017)       |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2017)     |

::: moniker-end

::: moniker range="vs-2019"

| Edition                    | Archivo                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Comunidad de Visual Studio    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)       |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |

::: moniker-end

### <a name="step-2---create-a-local-install-cache"></a>Paso 2: Crear una caché de instalación local

Deberá disponer de conexión a Internet para poder completar este paso.

> [!IMPORTANT]
> Si instala Visual Studio Community, debe activarlo antes de que transcurran 30 días desde la instalación. Esto requiere una conexión a Internet.

Abra un símbolo del sistema y use uno de los comandos de los ejemplos siguientes. En los ejemplos que se enumeran se asume que está usando la edición Community de Visual Studio; ajuste el comando según sea adecuado para su edición.

> [!TIP]
> Para evitar un error, asegúrese de que la ruta de acceso a la instalación completa tiene menos de 80 caracteres.

- Para el desarrollo web y de escritorio .NET, ejecute:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
    ```

- Para el desarrollo de escritorio .NET y Office, ejecute:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
    ```

- Para el desarrollo de escritorio C++, ejecute:

   ```cmd
    vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
    ```

- Para crear un diseño local completo con todas las características (lo que llevará mucho tiempo&mdash;, ya que tenemos _multitud_ de características), ejecute:

   ```cmd
    vs_community.exe --layout c:\vslayout --lang en-US
    ```

::: moniker range="vs-2017"

   > [!NOTE]
   > Un diseño completo de Visual Studio requiere como mínimo 35 GB de espacio en disco. Para más información, consulte [Requisitos del sistema](/visualstudio/productinfo/vs2017-system-requirements-vs/). Y para más información sobre cómo crear un diseño solo con los componentes que quiere instalar, consulte [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

::: moniker-end

::: moniker range="vs-2019"

   > [!NOTE]
   > Un diseño completo de Visual Studio requiere como mínimo 35 GB de espacio en disco. Para más información, consulte [Requisitos del sistema](/visualstudio/releases/2019/system-requirements/). Y para más información sobre cómo crear un diseño solo con los componentes que quiere instalar, consulte [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

::: moniker-end

Si quiere instalar un idioma distinto del inglés, cambie `en-US` a una configuración regional de la [lista de configuraciones regionales de idioma](#list-of-language-locales). Después, use la [lista de los componentes y cargas de trabajo disponibles](workload-and-component-ids.md) para personalizar aún más la memoria caché de instalación.

### <a name="step-3---install-visual-studio-from-the-local-cache"></a>Paso 3: Instalar Visual Studio desde la caché local

> [!TIP]
> Cuando se trabaja desde una caché de instalación local, el programa de instalación usa las versiones locales de cada uno de estos archivos. Pero si selecciona componentes durante la instalación que no se encuentran en la memoria caché, el programa de instalación intentará descargarlos de Internet.

Para asegurarse de que solo instala los archivos que ha descargado previamente, use las mismas opciones de la línea de comandos que usó para crear la memoria caché de diseño. Por ejemplo, si creó una caché de diseño con el siguiente comando:

```cmd
vs_community.exe --layout c:\vslayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

Después, use este comando para ejecutar la instalación:

```cmd
c:\vslayout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

> [!NOTE]
> Si se produce un error de una firma que no es válida, debe instalar certificados actualizados. Abra la carpeta de certificados en la caché sin conexión. Haga doble clic en cada uno de los archivos de certificado y, después, haga clic en el Asistente de administrador de certificados. Si se le solicita una contraseña, déjela en blanco.

### <a name="list-of-language-locales"></a>Lista de configuraciones regionales de idioma

| **Idioma-configuración regional** | **Lenguaje** |
| ----------------------- | --------------- |
| cs-CZ | Checo |
| de-DE | Alemán |
| en-US | English |
| es-ES | Español |
| fr-FR | Francés |
| it-IT | Italiano |
| ja-JP | Japonés |
| ko-KR | Coreano |
| pl-PL | Polaco |
| pt-BR | Portugués (Brasil) |
| ru-RU | Ruso |
| tr-TR | Turco |
| zh-CN | Chino (simplificado) |
| zh-TW | Chino (tradicional) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

- [Creación de una instalación de red de Visual Studio](../install/create-a-network-installation-of-visual-studio.md)
- [Actualizar una instalación basada en red de Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Instalar los certificados necesarios para la instalación sin conexión de Visual Studio](../install/install-certificates-for-visual-studio-offline.md)
- [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [Identificadores de cargas de trabajo y componentes de Visual Studio](workload-and-component-ids.md)
