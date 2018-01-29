---
title: "Instalación en entornos de red de bajo ancho de banda o poco confiables | Microsoft Docs"
description: "Se describe cómo funciona el instalador de Visual Studio en condiciones de red poco confiables y se explica cómo descargar archivos de instalación antes de comenzar la instalación."
ms.date: 01/17/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installing Visual Studio
- no internet connection
author: tglee
ms.author: tglee
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8b78f51c3b408d5a8c0723779cdf0b2d165aeec1
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2018
---
# <a name="install-visual-studio-2017-on-low-bandwidth-or-unreliable-network-environments"></a>Instalación de Visual Studio 2017 en entornos de red de bajo ancho de banda o poco confiables

Se recomienda probar el instalador web de Visual Studio; creemos que será una buena experiencia en la mayoría de los casos.

 > [!div class="button"]
 > [Descargar Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocsOL)
<br/>

Pero si la conexión a Internet no está disponible o no es confiable, puede usar la línea de comandos para crear una memoria caché local de los archivos que necesita para completar una instalación sin conexión. Esta es la manera de hacerlo.

> [!NOTE]
> Si es un administrador de empresa que quiere realizar una implementación de Visual Studio 2017 en una red de estaciones de trabajo del cliente con firewall desde Internet, vea las páginas [Creación de una instalación de red de Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) y [Instalar los certificados necesarios para la instalación sin conexión de Visual Studio](../install/install-certificates-for-visual-studio-offline.md).

## <a name="step-1---download-the-visual-studio-bootstrapper"></a>Paso 1: Descargar el programa previo de Visual Studio

Para comenzar, descargue el programa previo de Visual Studio para la edición elegida de Visual Studio.

Su archivo de instalación&mdash;o, para ser más exactos, un archivo de programa previo&mdash;corresponderá o será parecido a uno de los siguientes:

| Edición                    | Archivo                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Comunidad de Visual Studio    | [vs_community.exe](https://aka.ms/vs/15/release/vs_community.exe)       |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe)     |

## <a name="step-2---create-a-local-install-cache"></a>Paso 2: Crear una caché de instalación local

Deberá disponer de conexión a Internet para poder completar este paso. Para crear un diseño local, abra un símbolo del sistema y use uno de los comandos de los ejemplos siguientes: en estos ejemplos se supone que está usando la edición Community de Visual Studio; ajuste el comando según corresponda para su edición.

- Para el desarrollo web y de escritorio .NET, ejecute:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

- Para el desarrollo de escritorio .NET y Office, ejecute:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US```

- Para el desarrollo de escritorio C++, ejecute:

   ```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US```

- Para crear un diseño local completo con todas las características (lo que llevará mucho tiempo&mdash;, ya que tenemos _multitud_ de características), ejecute:

   ```vs_community.exe --layout c:\vs2017layout --lang en-US```

Si quiere instalar un idioma distinto del inglés, cambie `en-US` a una configuración regional de la lista en la parte inferior de esta página. Use esta [lista de los componentes y las cargas de trabajo disponibles](workload-and-component-ids.md) para personalizar aún más su caché de instalación según sea necesario.

> [!IMPORTANT]
> Un diseño de Visual Studio 2017 completo requiere al menos 35 GB de espacio en disco y puede tardar algún tiempo en descargarse. Vea [Usar parámetros de la línea de comandos para instalar Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) para más información sobre cómo crear un diseño solo con los componentes que quiere instalar.

## <a name="step-3---install-visual-studio-from-the-local-cache"></a>Paso 3: Instalar Visual Studio desde la caché local

> [!TIP]
> Cuando se trabaja desde una caché de instalación local, el programa de instalación usa las versiones locales de cada uno de estos archivos. Pero si selecciona componentes durante la instalación que no se encuentran en la caché, se intentará descargarlos de Internet.

Para asegurarse de que solo instala los archivos que ha descargado, use las mismas opciones de la línea de comandos que utilizó para crear la caché de diseño. Por ejemplo, si creó una caché de diseño con el siguiente comando:

```vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US```

Use este comando para ejecutar la instalación:

```c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional```

> [!NOTE]
> Si se produce un error de una firma que no es válida, debe instalar certificados actualizados. Abra la carpeta de certificados en la caché sin conexión. Haga doble clic en cada uno de los archivos de certificado y, después, haga clic en el Asistente de administrador de certificados. Si se le solicita una contraseña, déjela en blanco.

## <a name="list-of-language-locales"></a>Lista de configuraciones regionales de idioma

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
