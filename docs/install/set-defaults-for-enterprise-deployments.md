---
title: Establecimiento de valores predeterminados para implementaciones empresariales
description: Obtenga información sobre directivas de dominio y otras operaciones de configuración para implementaciones empresariales de Visual Studio.
ms.date: 03/30/2019
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
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d03912eecd7b3cfa3563fc095453fee3ddf9b163
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114280"
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

| **Name** | **ype** | **Predetermiado** | **Descripción** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` o `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | El directorio donde se almacenan los manifiestos de paquete y, opcionalmente, las cargas. Para más información, vea la página [Deshabilitación o traslado de la caché de paquetes](disable-or-move-the-package-cache.md). |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Mantenga instaladas las cargas de paquetes incluso después de estar instaladas. Puede cambiar el valor en cualquier momento. Al deshabilitar la directiva, se quitan las cargas de paquetes almacenadas en caché de la instancia reparada o modificada. Para más información, vea la página [Deshabilitación o traslado de la caché de paquetes](disable-or-move-the-package-cache.md). |
| `SharedInstallationPath` | `REG_SZ` o `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | El directorio donde están instalados algunos paquetes compartidos entre versiones de instancias de Visual Studio. Puede cambiar el valor en cualquier momento, pero el cambio solo afectará a futuras instalaciones. Los productos que ya están instalados en la ubicación antigua no se deben mover, ya que es posible que dejen de funcionar correctamente. |
| `BackgroundDownloadDisabled` |`REG_DWORD` | 1 | Impida que el programa de instalación descargue actualizaciones automáticamente relativas a cualquier producto de Visual Studio instalado. Puede cambiar el valor en cualquier momento. |

> [!IMPORTANT]
> Si cambia la directiva del registro `CachePath` después de una instalación, debe mover la caché de paquetes existente a la nueva ubicación y asegurarse de que esté protegida de forma que `SYSTEM` y `Administrators` tengan acceso de control total y `Everyone`, de lectura.
> Si no se mueve o no se protege la caché existente, es posible que las futuras instalaciones experimenten problemas.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

- [Instalación de Visual Studio](install-visual-studio.md)
- [Deshabilitar o mover la caché del paquete](disable-or-move-the-package-cache.md)
- [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
