---
title: Crear una instalación sin conexión de Visual Studio
description: Obtenga información sobre cómo instalar Visual Studio sin conexión cuando la conexión a internet no sea de confianza o disponga de poco ancho de banda.
ms.custom: ''
ms.date: 08/28/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 987584be6d2d0a2ee794622e64e989de9ea80334
ms.sourcegitcommit: b9a32c3d94b19e7344f4872bc026efd3157cf220
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46135583"
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>Crear una instalación sin conexión de Visual Studio 2017

Hemos diseñado Visual Studio 2017 para que funcione bien en una variedad de configuraciones de red y de equipos. Aunque se recomienda que pruebe el [instalador web de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) &mdash;que es un archivo pequeño y le permite estar actualizado con todas las correcciones y características más recientes&mdash; somos conscientes de que es posible que no pueda hacerlo.

Por ejemplo, puede que disponga de una conexión a Internet no confiable o de poco ancho de banda. Si es así, tiene varias opciones: puede usar la nueva característica "Download all, then install" (Descargar todo y volver a instalar) para descargar los archivos antes de instalar, o puede usar la línea de comandos para crear una caché local de los archivos.

> [!NOTE]
> Si es un administrador de empresa que quiere realizar una implementación de Visual Studio 2017 en una red de estaciones de trabajo del cliente con firewall desde Internet, vea las páginas [Creación de una instalación de red de Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) y [Instalar los certificados necesarios para la instalación sin conexión de Visual Studio](../install/install-certificates-for-visual-studio-offline.md).

## <a name="use-the-download-all-then-install-feature"></a>Usar la característica "Download all, then install" (Descargar todo y volver a instalar)

[**Novedad de la versión 15.8**](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&view=vs-2017#install
): después de descargar el instalador web, seleccione la nueva opción **"Download all, then install"** (Descargar todo y volver a instalar) desde el instalador de Visual Studio. Después, continúe con la instalación.

   ![Opción "Download all, then install" (Descargar todo y volver a instalar)](media/download-all-then-install.png)

## <a name="use-the-command-line-to-create-a-local-cache"></a>Usar la línea de comandos para crear una memoria caché local

Después de descargar un pequeño programa previo, use la línea de comandos para crear una memoria caché local. Después, use la memoria caché local para instalar Visual Studio. (Este proceso reemplaza los archivos ISO que había disponibles para las versiones anteriores).

Esta es la manera de hacerlo.

### <a name="step-1---download-the-visual-studio-bootstrapper"></a>Paso 1: Descargar el programa previo de Visual Studio

Deberá disponer de conexión a Internet para poder completar este paso.

Para comenzar, descargue el programa previo de Visual Studio para la edición elegida de Visual Studio. El archivo de instalación &mdash;o programa previo&mdash; corresponderá o será parecido a uno de los siguientes.

| Edición                    | Archivo                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Comunidad de Visual Studio    | [vs_community.exe](https://aka.ms/vs/15/release/vs_community.exe)       |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe)     |

### <a name="step-2---create-a-local-install-cache"></a>Paso 2: Crear una caché de instalación local

Deberá disponer de conexión a Internet para poder completar este paso.

Abra un símbolo del sistema y use uno de los comandos de los ejemplos siguientes. En los ejemplos que se enumeran se asume que está usando la edición Community de Visual Studio; ajuste el comando según sea adecuado para su edición.

- Para el desarrollo web y de escritorio .NET, ejecute:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

- Para el desarrollo de escritorio .NET y Office, ejecute:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US```

- Para el desarrollo de escritorio C++, ejecute:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US```

- Para crear un diseño local completo con todas las características (lo que llevará mucho tiempo&mdash;, ya que tenemos _multitud_ de características), ejecute:

   ```vs_community.exe --layout c:\vs2017layout --lang en-US```

Si quiere instalar un idioma distinto del inglés, cambie `en-US` a una configuración regional de la [lista de configuraciones regionales de idioma](#list-of-language-locales). Después, use la [lista de los componentes y cargas de trabajo disponibles](workload-and-component-ids.md) para personalizar aún más la memoria caché de instalación.

> [!IMPORTANT]
> Un diseño de Visual Studio 2017 completo requiere al menos 35 GB de espacio en disco y puede tardar algún tiempo en descargarse. Vea [Usar parámetros de la línea de comandos para instalar Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) para más información sobre cómo crear un diseño solo con los componentes que quiere instalar.

### <a name="step-3---install-visual-studio-from-the-local-cache"></a>Paso 3: Instalar Visual Studio desde la caché local

> [!TIP]
> Cuando se trabaja desde una caché de instalación local, el programa de instalación usa las versiones locales de cada uno de estos archivos. Pero si selecciona componentes durante la instalación que no se encuentran en la memoria caché, el programa de instalación intentará descargarlos de Internet.

Para asegurarse de que solo instala los archivos que ha descargado previamente, use las mismas opciones de la línea de comandos que usó para crear la memoria caché de diseño. Por ejemplo, si creó una caché de diseño con el siguiente comando:

```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

Después, use este comando para ejecutar la instalación:

```c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional```

> [!NOTE]
> Si se produce un error de una firma que no es válida, debe instalar certificados actualizados. Abra la carpeta de certificados en la caché sin conexión. Haga doble clic en cada uno de los archivos de certificado y, después, haga clic en el Asistente de administrador de certificados. Si se le solicita una contraseña, déjela en blanco.

### <a name="list-of-language-locales"></a>Lista de configuraciones regionales de idioma

| **Idioma-configuración regional** | **Idioma** |
| ----------------------- | --------------- |
| cs-CZ | Checo |
| de-DE | Alemán |
| en-US | Inglés |
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

- [Creación de una instalación de red de Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md)
- [Instalar los certificados necesarios para la instalación sin conexión de Visual Studio](../install/install-certificates-for-visual-studio-offline.md)
- [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [Identificadores de componente y carga de trabajo de Visual Studio 2017](workload-and-component-ids.md)
