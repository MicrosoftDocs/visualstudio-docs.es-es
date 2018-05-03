---
title: Establecimiento de valores predeterminados para implementaciones empresariales de Visual Studio
description: Obtenga información sobre directivas de dominio y otras operaciones de configuración para implementaciones empresariales de Visual Studio.
ms.date: 05/05/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f229ea889a478281ee0db123da00cd67c82ec13a
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
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

| **Name** | **Type** | **Predetermiado** | **Descripción** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` o `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | El directorio donde se almacenan los manifiestos de paquete y, opcionalmente, las cargas. Para más información, lea cómo [deshabilitar o mover la caché de paquetes](disable-or-move-the-package-cache.md). |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Mantenga instaladas las cargas de paquetes incluso después de estar instaladas. Puede cambiar el valor en cualquier momento. Al deshabilitar la directiva, se quitan las cargas de paquetes almacenadas en caché de la instancia reparada o modificada. Para más información, lea cómo [deshabilitar o mover la caché de paquetes](disable-or-move-the-package-cache.md). |
| `SharedInstallationPath` | `REG_SZ` o `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | El directorio donde están instalados algunos paquetes compartidos entre versiones de instancias de Visual Studio. Puede cambiar el valor en cualquier momento, pero dicho cambio solo afectará a futuras instalaciones. Los productos que ya están instalados en la ubicación antigua no se deben mover ya que podrían dejar de funcionar correctamente. |

> [!IMPORTANT]
> Si cambia la directiva del Registro `CachePath` después de una instalación, debe mover la caché de paquetes existente a la nueva ubicación y asegurarse de que está protegida de forma que `SYSTEM` y `Administrators` tengan control completo y `Everyone` tenga acceso de lectura.
> Si no se mueve o no se protege la caché existente, las futuras instalaciones podrían experimentar problemas.

## <a name="get-support"></a>Obtener soporte técnico

En ocasiones, algo no sale según lo previsto. Si se produce un error en la instalación de Visual Studio, consulte la página [Troubleshooting Visual Studio 2017 installation and upgrade issues](troubleshooting-installation-issues.md) (Solucionar problemas de errores de instalación y actualización de Visual Studio 2017). Si ninguno de los pasos de solución de problemas ayuda, puede ponerse en contacto con nosotros por chat para obtener asistencia para la instalación (solo en inglés). Para más información, consulte la [página de soporte técnico de Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Aquí tiene algunas opciones de soporte técnico más:

* Puede notificarnos problemas del producto a través de la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) que aparece en el instalador y en el IDE de Visual Studio.
* Puede compartir una sugerencia de producto con nosotros en [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Puede realizar el seguimiento de los problemas del producto y encontrar respuestas en la [comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/).
* También puede ponerse en contacto con nosotros y otros desarrolladores de Visual Studio a través de la [conversación de Visual Studio en la comunidad de Gitter](https://gitter.im/Microsoft/VisualStudio). (Esta opción requiere una cuenta de [GitHub](https://github.com/)).

## <a name="see-also"></a>Vea también

 * [Instalar Visual Studio](install-visual-studio.md)
 * [Deshabilitar o mover la caché del paquete](disable-or-move-the-package-cache.md)
 * [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
