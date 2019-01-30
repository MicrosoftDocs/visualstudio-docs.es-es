---
title: Quitar Visual Studio
titleSuffix: ''
description: Obtenga información detallada sobre cómo quitar completamente Visual Studio del equipo.
ms.date: 09/12/2017
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- uninstall
- uninstall Visual Studio
- remove
- remove Visual Studio
- cleanup
- cleanup Visual Studio
- clean up
- clean up Visual Studio
ms.assetid: 9c81a777-9c95-4934-b517-c60c6dc78799
author: heaths
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc3aad95042b59a18df0d805ce11ac5e2f0518ff
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009848"
---
# <a name="remove-visual-studio-2017"></a>Eliminación de Visual Studio 2017

Si se produce un error grave y no se puede reparar o desinstalar Visual Studio, puede ejecutar la herramienta `InstallCleanup.exe` para quitar los archivos de instalación y la información de producto de todas las instancias instaladas de Visual Studio 2017 y versiones más recientes. La ejecución de esta herramienta debe hacerse como último recurso si se produce un error en la reparación o desinstalación, y puede desinstalar características de otras instalaciones de Visual Studio u otros productos que sea necesario reparar.

En las instrucciones siguientes, puede ejecutar la herramienta con distintos modificadores de línea de comandos con el comportamiento siguiente:

| Modificador | Comportamiento |
| ------ | -------- |
| `-i`   | Este modificador es el predeterminado si no se pasa ningún otro modificador y solo quita el directorio de instalación principal y la información del producto. Este comportamiento es preferible si piensa volver a instalar la misma versión después de ejecutar la herramienta `InstallCleanup.exe`. |
| `-f`   | Especificar este modificador quita el directorio de instalación principal, la información del producto y la mayoría de características instaladas fuera del directorio de instalación que pueden estar compartidas con otras instalaciones de Visual Studio u otros productos. Este comportamiento es preferible si piensa quitar Visual Studio sin volverlo a instalar más adelante. |

1. Cierre el instalador de Visual Studio.
2. Abra un símbolo del sistema de administrador. Para abrir un símbolo del sistema de administrador, siga estos pasos:
   * Haga clic en el menú **Inicio**.
   * Escriba **cmd**.
   * Haga clic con el botón derecho en **Símbolo del sistema** y, después, haga clic en **Ejecutar como administrador**.
3. Escriba la ruta de acceso completa de la utilidad `InstallCleanup.exe` y pase el modificador de línea de comandos que quiera. De forma predeterminada, la ruta de acceso de la utilidad es la siguiente:
   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```

Si no encuentra `InstallCleanup.exe` en el directorio del Instalador de Visual Studio (siempre se ubica en `%ProgramFiles(x86)%\Microsoft Visual Studio`) siga las instrucciones para [instalar Visual Studio](install-visual-studio.md) y cuando aparezca la pantalla de selección de la carga de trabajo, cierre la ventana y siga de nuevo los pasos anteriores.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Instalación de Visual Studio 2017](install-visual-studio.md)
* [Actualizar Visual Studio 2017](update-visual-studio.md)
* [Modificación de Visual Studio 2017](modify-visual-studio.md)
* [Desinstalación de Visual Studio 2017](uninstall-visual-studio.md)
