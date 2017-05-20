---
title: "Establecimiento de valores predeterminados para la implementación empresarial de Visual Studio | Microsoft Docs"
description: "Directivas de dominio y otras operaciones de configuración para la implementación empresarial de Visual Studio."
ms.date: 05/05/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
author: heaths
ms.author: heaths
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 8f38b2707376d4bee8852ad107980fa925114d99
ms.openlocfilehash: 05c5fd9e4be4cbf7d40e27c7c97793bc2466efe3
ms.contentlocale: es-es
ms.lasthandoff: 05/05/2017

---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Establecimiento de valores predeterminados para implementaciones empresariales de Visual Studio

Puede establecer directivas de Registro que afectan a la implementación de Visual Studio. Estas directivas son globales para el nuevo instalador y afectan a:

- Donde se hayan instalado algunos paquetes compartidos con otras versiones o instancias
- Donde se almacenan en caché los paquetes
- Si todos los paquetes se almacenan en caché

Puede establecer algunas de estas directivas mediante [opciones de línea de comandos](use-command-line-parameters-to-install-visual-studio.md), configurar valores del Registro en su máquina o incluso distribuirlas mediante directiva de grupos en una organización.

## <a name="registry-keys"></a>Claves del Registro

Hay varios lugares donde puede establecer valores predeterminados de empresa, para permitir su control mediante directiva de grupo o directamente en el Registro. Visual Studio comprueba secuencialmente si se han establecido directivas de empresa; en cuanto se descubre un valor de directiva en el orden siguiente, el resto de claves se ignora.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup` (en sistemas operativos de 64 bits)

Si no se han establecido ya, algunos valores del Registro se establecerán automáticamente la primera vez que se usen. De esta forma se garantiza que las instalaciones posteriores usarán los mismos valores. Estos se almacenarán en la segunda clave del Registro, `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`.

Puede establecer los siguientes valores del Registro.

| **Name** | **Type** | **Predetermiado** | **Descripción** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` o `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | El directorio donde se almacenan los manifiestos de paquete y, opcionalmente, las cargas. Para más información, lea cómo [deshabilitar o mover la caché de paquetes](disable-or-move-the-package-cache.md). |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Mantenga instaladas las cargas de paquetes incluso después de estar instaladas. Puede cambiar el valor en cualquier momento. Al deshabilitar la directiva, se quitan las cargas de paquetes almacenadas en caché de la instancia reparada o modificada. Para más información, lea cómo [deshabilitar o mover la caché de paquetes](disable-or-move-the-package-cache.md). |
| `SharedInstallationPath` | `REG_SZ` o `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | El directorio donde están instalados algunos paquetes compartidos entre versiones de instancias de Visual Studio. Puede cambiar el valor en cualquier momento, pero dicho cambio solo afectará a futuras instalaciones. Los productos que ya están instalados en la ubicación antigua no se deben mover ya que podrían dejar de funcionar correctamente. |

> [!IMPORTANT]
> Si cambia la directiva del Registro `CachePath` después de una instalación, debe mover la caché de paquetes existente a la nueva ubicación y asegurarse de que está protegida de forma que `SYSTEM` y `Administrators` tengan control completo y `Everyone` tenga acceso de lectura.
> Si no se mueve o no se protege la caché existente, las futuras instalaciones podrían experimentar problemas.

## <a name="see-also"></a>Vea también

 * [Instalar Visual Studio](install-visual-studio.md)
 * [Deshabilitar o mover la caché del paquete](disable-or-move-the-package-cache.md)
 * [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [Notificar un problema con Visual Studio](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

