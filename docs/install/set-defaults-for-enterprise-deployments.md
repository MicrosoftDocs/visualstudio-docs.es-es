---
title: Establecimiento de valores predeterminados para implementaciones empresariales
description: Obtenga información sobre directivas de dominio y otras operaciones de configuración para implementaciones empresariales de Visual Studio.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 9d3d6f658e3d24f3c82737c0c457323b9d4eb4b6
ms.sourcegitcommit: 56060e3186086541d9016d4185e6f1bf3471e958
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/07/2021
ms.locfileid: "106547471"
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Establecimiento de valores predeterminados para implementaciones empresariales de Visual Studio

Puede establecer directivas de Registro que afectan a la implementación de Visual Studio. Estas directivas son globales para el nuevo instalador y afectan a:

- Donde se hayan instalado algunos paquetes compartidos con otras versiones o instancias
- Donde se almacenan en caché los paquetes
- Si todos los paquetes se almacenan en caché

Puede establecer algunas de estas directivas mediante [opciones de línea de comandos](use-command-line-parameters-to-install-visual-studio.md), configurar valores del Registro en su equipo o incluso distribuirlas mediante la directiva de grupos en una organización.

## <a name="registry-keys"></a>Claves del Registro

Hay varios lugares donde puede establecer valores predeterminados de empresa, para permitir su control mediante directiva de grupo o directamente en el Registro. Visual Studio comprueba secuencialmente si se han establecido directivas de empresa; en cuanto se descubre un valor de directiva en el orden siguiente, el resto de claves se ignora.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup` (en sistemas operativos de 64 bits)

> [!IMPORTANT]
> Si no establece la clave `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup` y, en su lugar, establece una de las otras claves, debe establecer las otras claves en los sistemas operativos de 64 bits. Este problema se resuelve en una actualización futura del producto.

Si todavía no se han establecido, algunos valores del Registro se establecen automáticamente la primera vez que se usan. Esta práctica garantiza que en las instalaciones posteriores se usarán los mismos valores. Estos se almacenan en la segunda clave del Registro, `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`.

Puede establecer los siguientes valores del Registro:

::: moniker range="vs-2017"
| **Nombre** | **Tipo** | **Valor predeterminado** | **Descripción** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` o `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | El directorio donde se almacenan los manifiestos de paquete y, opcionalmente, las cargas. Para más información, consulte la página [Deshabilitación o traslado de la caché de paquetes](disable-or-move-the-package-cache.md). |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Mantenga instaladas las cargas de paquetes incluso después de estar instaladas. Puede cambiar el valor en cualquier momento. Al deshabilitar la directiva, se quitan las cargas de paquetes almacenadas en caché de la instancia reparada o modificada. Para más información, consulte la página [Deshabilitación o traslado de la caché de paquetes](disable-or-move-the-package-cache.md). |
| `SharedInstallationPath` | `REG_SZ` o `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | El directorio donde están instalados algunos paquetes compartidos entre versiones de instancias de Visual Studio. Puede cambiar el valor en cualquier momento, pero el cambio solo afectará a las futuras instalaciones. Los productos que ya están instalados en la ubicación antigua no se deben mover, ya que es posible que dejen de funcionar correctamente. |
| `BackgroundDownloadDisabled` |`REG_DWORD` | 1 | Impida que el programa de instalación descargue actualizaciones automáticamente relativas a cualquier producto de Visual Studio instalado. Puede cambiar el valor en cualquier momento. |
| `AdministratorUpdatesEnabled` | `REG_DWORD` | 1 | Permite aplicar actualizaciones de administrador al equipo cliente. Si este valor falta o está establecido en 0, se bloquearán las actualizaciones de administrador. Este valor es para uso administrativo. Para más información, consulte [Habilitación de actualizaciones de administrador](enabling-administrator-updates.md). | 
| `AdministratorUpdatesOptOut` | `REG_DWORD` | 1 | Indica que el usuario no quiere recibir actualizaciones de administrador en Visual Studio. La ausencia de la clave del Registro, o un valor establecido de 0, significa que el usuario de Visual Studio quiere recibir actualizaciones de administrador en Visual Studio. Esta opción va dirigida a los usuarios desarrolladores (si tienen permisos de administrador en la máquina cliente). Para más información, consulte [Aplicación de actualizaciones de administrador](../install/applying-administrator-updates.md#understanding-configuration-options). | 
| `UpdateConfigurationFile` | `REG_SZ` o `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\updates.config | La ruta de acceso de archivo para configurar las actualizaciones administrativas. Para más información, consulte [Métodos para configurar una actualización de administrador](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update). | 
::: moniker-end

::: moniker range="vs-2019"
| **Nombre** | **Tipo** | **Valor predeterminado** | **Descripción** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` o `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | El directorio donde se almacenan los manifiestos de paquete y, opcionalmente, las cargas. Para más información, consulte la página [Deshabilitación o traslado de la caché de paquetes](disable-or-move-the-package-cache.md). |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Mantenga instaladas las cargas de paquetes incluso después de estar instaladas. Puede cambiar el valor en cualquier momento. Al deshabilitar la directiva, se quitan las cargas de paquetes almacenadas en caché de la instancia reparada o modificada. Para más información, consulte la página [Deshabilitación o traslado de la caché de paquetes](disable-or-move-the-package-cache.md). |
| `SharedInstallationPath` | `REG_SZ` o `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | El directorio donde están instalados algunos paquetes compartidos entre versiones de instancias de Visual Studio. Puede cambiar el valor en cualquier momento, pero el cambio solo afectará a las futuras instalaciones. Los productos que ya están instalados en la ubicación antigua no se deben mover, ya que es posible que dejen de funcionar correctamente. |
| `BackgroundDownloadDisabled` |`REG_DWORD` | 1 | Impida que el programa de instalación descargue actualizaciones automáticamente relativas a cualquier producto de Visual Studio instalado. Puede cambiar el valor en cualquier momento. |
| `AdministratorUpdatesEnabled` | `REG_DWORD` | 1 | Permite aplicar actualizaciones de administrador al equipo cliente. Si este valor falta o está establecido en 0, se bloquearán las actualizaciones de administrador. Este valor es para uso administrativo. Para más información, consulte [Habilitación de actualizaciones de administrador](enabling-administrator-updates.md). | 
| `AdministratorUpdatesOptOut` | `REG_DWORD` | 1 | Indica que el usuario no quiere recibir actualizaciones de administrador en Visual Studio. La ausencia de la clave del Registro, o un valor establecido de 0, significa que el usuario de Visual Studio quiere recibir actualizaciones de administrador en Visual Studio. Esta opción va dirigida a los usuarios desarrolladores (si tienen permisos de administrador en la máquina cliente). Para más información, consulte [Aplicación de actualizaciones de administrador](../install/applying-administrator-updates.md#understanding-configuration-options). | 
| `UpdateConfigurationFile` | `REG_SZ` o `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\updates.config | La ruta de acceso de archivo para configurar las actualizaciones administrativas. Para más información, consulte [Métodos para configurar una actualización de administrador](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update). | 
| `BaselineStickinessVersions2019` | `REG_SZ` o `REG_EXPAND_SZ` | `ALL` o `16.4.0,16.7.0,16.9.0` | Las versiones que autorizan que las actualizaciones permanezcan en las líneas de base de servicio especificadas. Para más información, consulte la página [Aplicación de actualizaciones de administrador](../install/applying-administrator-updates.md#understanding-configuration-options). | 
::: moniker-end

> [!IMPORTANT]
> Si cambia la directiva del registro `CachePath` después de una instalación, debe mover la caché de paquetes existente a la nueva ubicación y asegurarse de que esté protegida de forma que `SYSTEM` y `Administrators` tengan acceso de control total y `Everyone`, de lectura.
> Si no se mueve o no se protege la caché existente, es posible que las futuras instalaciones experimenten problemas.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Consulte también

- [Instalación de Visual Studio](install-visual-studio.md)
- [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
- [Deshabilitación o traslado de la caché de paquetes](disable-or-move-the-package-cache.md)
- [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
