---
title: Herramientas para detectar y administrar instancias de Visual Studio
titleSuffix: ''
description: Obtenga información sobre las herramientas que puede usar para detectar y administrar instalaciones de Visual Studio en equipos cliente.
ms.date: 08/14/2017
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 006a3fa3d41799a87449b8f9e111ca341a698bf5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935417"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Herramientas para detectar y administrar instancias de Visual Studio

Hay varias herramientas que puede usar para detectar instalaciones de Visual Studio en equipos cliente y también para administrar las instalaciones.

## <a name="detecting-existing-visual-studio-instances"></a>Detección de instancias existentes de Visual Studio

Dispone de varias herramientas que le ayudarán a detectar y administrar las instancias de Visual Studio instaladas en los equipos cliente:

* [vswhere](https://github.com/microsoft/vswhere): un archivo ejecutable integrado en Visual Studio o disponible para su distribución independiente que le ayuda a encontrar la ubicación de todas las instancias de Visual Studio en un equipo determinado.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): scripts de PowerShell que usan la API de configuración de la instalación para identificar las instancias instaladas de Visual Studio.
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples): ejemplos de C# y C++ en los que se muestra cómo usar la API de configuración de la instalación para consultar una instalación existente.

Además, la [API de configuración de la instalación](<xref:Microsoft.VisualStudio.Setup.Configuration>) proporciona interfaces para los desarrolladores que quieran crear sus propias utilidades para interrogar instancias de Visual Studio.

## <a name="using-vswhereexe"></a>Uso de vswhere.exe

`vswhere.exe` se incluye automáticamente en Visual Studio (a partir de Visual Studio 2017 versión 15.2 y versiones posteriores) o puede descargarlo desde la [página de versiones de vswhere](https://github.com/Microsoft/vswhere/releases). Use `vswhere -?` para obtener información de ayuda sobre la herramienta. Por ejemplo, este comando muestra todas las versiones de Visual Studio, incluidas las versiones anteriores del producto y versiones preliminares, y muestra los resultados en formato JSON:

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

::: moniker range="vs-2017"

> [!TIP]
> Para obtener más información sobre la instalación de Visual Studio 2017, vea [Visual Studio Setup Archives](https://devblogs.microsoft.com/setup/tag/vs2017/) (Archivos de instalación de Visual Studio).

::: moniker-end

## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Edición del Registro para una instancia de Visual Studio

En Visual Studio, la configuración del Registro se almacena en una ubicación privada, lo que permite varias instancias en paralelo de la misma versión de Visual Studio en la misma máquina.

Como estas entradas no se almacenan en el Registro global, hay instrucciones especiales para usar el Editor del Registro para realizar cambios en su configuración:

1. Si tiene abierta una instancia de Visual Studio, ciérrela.

1. Inicie `regedit.exe`.

1. Seleccione el nodo `HKEY_LOCAL_MACHINE`.

1. En el menú principal de Regedit, seleccione **Archivo** > **Cargar subárbol...** y luego seleccione el archivo de Registro privado, que se encuentra almacenado en la carpeta **AppData\Local**. Por ejemplo:

   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>` corresponde a la instancia de Visual Studio que le gustaría examinar.

Se le pedirá que proporcione un nombre de subárbol, que se convertirá en el nombre de su subárbol aislado. Después de haber hecho esto, debería poder examinar el Registro bajo el subárbol aislado que creó.

> [!IMPORTANT]
> Antes de iniciar de nuevo Visual Studio, debe descargar el subárbol aislado que creó. Para ello, seleccione **Archivo** > **Descargar subárbol** desde el menú principal de Regedit. (Si no lo hace, el archivo permanece bloqueado y Visual Studio no se podrá iniciar).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Guía de administradores de Visual Studio](visual-studio-administrator-guide.md)
