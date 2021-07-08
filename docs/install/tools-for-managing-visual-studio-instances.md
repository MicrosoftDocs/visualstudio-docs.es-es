---
title: Herramientas para detectar y administrar instancias de Visual Studio
titleSuffix: ''
description: Obtenga información sobre las herramientas que puede usar para detectar y administrar instalaciones de Visual Studio en equipos cliente.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 914449fe1db792614af1f9ed22464cb9fdb91481
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306896"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Herramientas para detectar y administrar instancias de Visual Studio

Hay varias herramientas que puede usar para detectar instalaciones de Visual Studio en máquinas cliente y también para administrar las instalaciones.

## <a name="detecting-existing-visual-studio-instances"></a>Detección de instancias existentes de Visual Studio

Las siguientes herramientas y utilidades le ayudarán a detectar y administrar las instancias de Visual Studio instaladas en las máquinas cliente:

* [**vswhere**](https://github.com/microsoft/vswhere): un archivo ejecutable integrado en Visual Studio o disponible para su distribución independiente que le ayuda a encontrar la ubicación de todas las instancias de Visual Studio en una máquina determinada.
* [**VSSetup.PowerShell**](https://github.com/microsoft/vssetup.powershell): scripts de PowerShell que usan la API de configuración de la instalación para identificar las instancias instaladas de Visual Studio.
* [**VS-Setup-Samples**](https://github.com/microsoft/vs-setup-samples): ejemplos de C# y C++ que muestran cómo usar la API de configuración de la instalación para consultar una instalación existente.
* [**Instrumental de administración de Windows (WMI)**](/windows/win32/wmisdk/wmi-start-page): la información de la instancia de Visual Studio se puede consultar mediante la clase MSFT_VSInstance de Visual Studio.
* Además, la [**API de configuración de la instalación**](<xref:Microsoft.VisualStudio.Setup.Configuration>) proporciona interfaces para los desarrolladores que quieran crear sus propias utilidades para interrogar instancias de Visual Studio.
* [**Inventario de software de Microsoft Endpoint Configuration Manager**](/mem/configmgr/core/clients/manage/inventory/introduction-to-software-inventory): se puede usar para recopilar información sobre las instancias de Visual Studio en los dispositivos cliente.

## <a name="using-vswhereexe"></a>Uso de vswhere.exe

`vswhere.exe` se incluye automáticamente en Visual Studio 2017 y posterior, o bien puede descargarlo en [la página de versiones de vswhere](https://github.com/Microsoft/vswhere/releases). Use `vswhere -?` para obtener información de ayuda sobre la herramienta. Por ejemplo, este comando muestra todas las versiones de Visual Studio, incluidas las versiones anteriores del producto y versiones preliminares, y muestra los resultados en formato JSON:

```shell
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

## <a name="using-windows-management-instrumentation-wmi"></a>Uso del Instrumental de administración de Windows (WMI)

Si la utilidad de detección de clientes de Visual Studio está instalada en la máquina, puede consultar la información de la instancia de Visual Studio mediante WMI. La utilidad de detección de clientes de Visual Studio se instala de forma predeterminada con cada actualización de Visual Studio 2017, Visual Studio 2019 y Visual Studio 2022 que se haya publicado desde el 12 de mayo de 2020. También está disponible en el [Catálogo de Microsoft Update](https://catalog.update.microsoft.com/) si quiere instalarla de forma independiente.  Para ver un ejemplo de cómo usar la utilidad para devolver información de la instancia de Visual Studio, abra PowerShell como administrador en la máquina cliente y escriba el siguiente comando:

```shell
Get-CimInstance MSFT_VSInstance
```

## <a name="using-microsoft-endpoint-configuration-manager"></a>Uso de Microsoft Endpoint Configuration Manager

Las funcionalidades de [inventario de software de Microsoft Endpoint Configuration Manager](/mem/configmgr/core/clients/manage/inventory/introduction-to-software-inventory) se pueden usar para consultar y recopilar información sobre las instancias de Visual Studio en los dispositivos cliente. Por ejemplo, la siguiente consulta devolverá el nombre para mostrar, la versión y el nombre del dispositivo en el que está instalado Visual Studio para todas las instancias instaladas de Visual Studio 2017 y 2019:

```WQL
select distinct SMS_G_System_COMPUTER_SYSTEM.Name, SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName, SMS_G_System_ADD_REMOVE_PROGRAMS.Version from SMS_R_System inner join SMS_G_System_COMPUTER_SYSTEM on SMS_G_System_COMPUTER_SYSTEM.ResourceID = SMS_R_System.ResourceId inner join SMS_G_System_ADD_REMOVE_PROGRAMS on SMS_G_System_ADD_REMOVE_PROGRAMS.ResourceID = SMS_R_System.ResourceId where SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName like "Visual Studio %[a-z]% 201[7,9]" 
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

   ```shell
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>` corresponde a la instancia de Visual Studio que le gustaría examinar.

Se le pedirá que proporcione un nombre de subárbol, que se convertirá en el nombre de su subárbol aislado. Después de haber hecho esto, debería poder examinar el Registro bajo el subárbol aislado que creó.

> [!IMPORTANT]
> Antes de iniciar de nuevo Visual Studio, debe descargar el subárbol aislado que creó. Para ello, seleccione **Archivo** > **Descargar subárbol** desde el menú principal de Regedit. (Si no lo hace, el archivo permanece bloqueado y Visual Studio no se podrá iniciar).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Guía del administrador de Visual Studio](../install/visual-studio-administrator-guide.md)
