---
title: Herramientas para detectar y administrar instancias de Visual Studio
description: Obtenga información sobre las herramientas que puede usar para detectar y administrar instalaciones de Visual Studio en equipos cliente.
ms.date: 08/14/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7052908751058b08be8afc3f1c40123ca8ddba48
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/20/2018
ms.locfileid: "36280580"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Herramientas para detectar y administrar instancias de Visual Studio

Hay varias herramientas que puede usar para detectar instalaciones de Visual Studio en equipos cliente y también para administrar las instalaciones.

## <a name="detecting-existing-visual-studio-instances"></a>Detección de instancias existentes de Visual Studio

Dispone de varias herramientas que le ayudarán a detectar y administrar las instancias de Visual Studio instaladas en los equipos cliente:

* [VSWhere](https://github.com/microsoft/vswhere): un archivo ejecutable integrado en Visual Studio o disponible para su distribución independiente que le ayuda a encontrar la ubicación de todas las instancias de Visual Studio en un equipo determinado.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): scripts de PowerShell que usan la API de configuración de la instalación para identificar las instancias instaladas de Visual Studio.
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples): ejemplos de C# y C++ que muestran cómo usar la API de configuración de la instalación para consultar una instalación existente.

Además, la [API de configuración de la instalación](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.setup.configuration.aspx) proporciona interfaces para los desarrolladores que quieran crear sus propias utilidades para interrogar instancias de Visual Studio.

## <a name="using-vswhereexe"></a>Uso de vswhere.exe

`vswhere.exe` se incluye automáticamente en Visual Studio 2017 versión 15.2 o posterior, o bien puede descargarlo en [la página de versiones](https://github.com/Microsoft/vswhere/releases). Use `vswhere -?` para obtener información de ayuda sobre la herramienta. Por ejemplo, este comando muestra todas las versiones de Visual Studio, incluidas las versiones anteriores del producto y versiones preliminares, y muestra los resultados en formato JSON:

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

>[!TIP]
>Para más información sobre la instalación de Visual Studio 2017, vea los [artículos del blog de Heath Stewart](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/).


## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Edición del Registro para una instancia de Visual Studio

En Visual Studio de 2017, configuración del Registro se almacena en una ubicación privada, lo que permite varias instancias en paralelo de la misma versión de Visual Studio en la misma máquina.

Como estas entradas no se almacenan en el Registro global, hay instrucciones especiales para usar el Editor del Registro para realizar cambios en su configuración:

1. Si tiene abierta una instancia de Visual Studio 2017, ciérrela.
2. Inicie `regedit.exe`.
3. Seleccione el nodo `HKEY_LOCAL_MACHINE`.
4. En el menú principal de Regedit, seleccione **Archivo -> Cargar subárbol ...** y luego seleccione el archivo de Registro privado, que se encuentra almacenado en la carpeta **AppData\Local**. Por ejemplo:
   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

  > [!NOTE]
  > `<config>` corresponde a la instancia de Visual Studio que le gustaría examinar.

Se le pedirá que proporcione un nombre de subárbol, que se convertirá en el nombre de su subárbol aislado. Después de haber hecho esto, debería poder examinar el Registro bajo el subárbol aislado que creó.

> [!IMPORTANT]
> Antes de iniciar de nuevo Visual Studio, debe descargar el subárbol aislado que creó. Para ello, seleccione Archivo -> Descargar subárbol desde el menú principal de Regedit. (Si no lo hace, el archivo permanece bloqueado y Visual Studio no se podrá iniciar).

## <a name="get-support"></a>Obtener soporte técnico

En ocasiones, algo no sale según lo previsto. Si se produce un error en la instalación de Visual Studio, consulte la página [Troubleshooting Visual Studio 2017 installation and upgrade issues](troubleshooting-installation-issues.md) (Solucionar problemas de errores de instalación y actualización de Visual Studio 2017). Si ninguno de los pasos de solución de problemas ayuda, puede ponerse en contacto con nosotros por chat para obtener asistencia para la instalación (solo en inglés). Para más información, consulte la [página de soporte técnico de Visual Studio](https://visualstudio.microsoft.com/vs/support/#talktous).

Aquí tiene algunas opciones de soporte técnico más:

* Puede notificarnos problemas del producto a través de la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) que aparece en el instalador y en el IDE de Visual Studio.
* Puede compartir una sugerencia de producto con nosotros en [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Puede realizar el seguimiento de los problemas del producto y encontrar respuestas en la [comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/).
* También puede ponerse en contacto con nosotros y otros desarrolladores de Visual Studio a través de la [conversación de Visual Studio en la comunidad de Gitter](https://gitter.im/Microsoft/VisualStudio). (Esta opción requiere una cuenta de [GitHub](https://github.com/)).

## <a name="see-also"></a>Vea también

* [Guía de administradores de Visual Studio](visual-studio-administrator-guide.md)
