---
title: Quitar Visual Studio 2017 | Microsoft Docs
description: "Obtenga información paso a paso sobre cómo quitar Visual Studio."
ms.custom: 
ms.date: 09/12/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
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
ms.author: heaths
manager: erickn
ms.openlocfilehash: 3c859b0023c9ea282afde837b17b7c93f3f4fbd7
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2017
---
# <a name="remove-visual-studio"></a>Quitar Visual Studio

Si se produce un error grave y no se puede reparar o desinstalar Visual Studio, puede ejecutar la herramienta `InstallCleanup.exe` para quitar los archivos de instalación y la información de producto. La ejecución de esta herramienta debe hacerse como último recurso si se produce un error en la reparación o desinstalación, y puede desinstalar características de otras instalaciones de Visual Studio u otros productos que sea necesario reparar.

En las instrucciones siguientes, puede ejecutar la herramienta con distintos modificadores de línea de comandos con el comportamiento siguiente:

| Modificador | Comportamiento |
| ------ | -------- |
| `-i`   | Este modificador es el predeterminado si no se pasa ningún otro modificador y solo quita el directorio de instalación principal y la información del producto. Este comportamiento es preferible si piensa volver a instalar la misma versión después de ejecutar la herramienta `InstallCleanup.exe`. |
| `-f`   | Especificar este modificador quita el directorio de instalación principal, la información del producto y la mayoría de características instaladas fuera del directorio de instalación que pueden estar compartidas con otras instalaciones de Visual Studio u otros productos. Este comportamiento es preferible si piensa quitar Visual Studio sin volverlo a instalar más adelante. |

1. Cierre el instalador de Visual Studio.
2. Abra un símbolo del sistema de administrador. Para abrir un símbolo del sistema de administrador, siga estos pasos:
   * En el menú **Inicio**, haga clic en **Ejecutar** (Inicio + R).
   * Escriba **cmd**.
   * Haga clic con el botón derecho en **Símbolo del sistema** y, después, haga clic en **Ejecutar como administrador**.
3. Escriba la ruta de acceso completa de la utilidad `InstallCleanup.exe` y pase el modificador de línea de comandos que quiera. De forma predeterminada, la ruta de acceso de la utilidad es la siguiente:
   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```

Si no encuentra `InstallCleanup.exe` en el directorio del Instalador de Visual Studio (siempre se ubica en `%ProgramFiles(x86)%\Microsoft Visual Studio`) siga las instrucciones para [instalar Visual Studio](install-visual-studio.md) y cuando aparezca la pantalla de selección de la carga de trabajo, cierre la ventana y siga de nuevo los pasos anteriores.

## <a name="get-support"></a>Obtener soporte técnico
En ocasiones, algo no sale según lo previsto. Si se produce un error en la instalación de Visual Studio, consulte la página [Troubleshooting Visual Studio 2017 installation and upgrade issues](troubleshooting-installation-issues.md) (Solucionar problemas de errores de instalación y actualización de Visual Studio 2017). Si ninguno de los pasos de solución de problemas ayuda, puede ponerse en contacto con nosotros por chat para obtener asistencia para la instalación (solo en inglés). Para más información, consulte la [página de soporte técnico de Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Aquí tiene algunas opciones de soporte técnico más:
* Puede notificarnos problemas del producto a través de la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) que aparece en el instalador y en el IDE de Visual Studio.
* Puede compartir una sugerencia de producto con nosotros en [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Puede realizar el seguimiento de los problemas del producto en la [comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/), y hacer preguntas y encontrar respuestas.
* También puede ponerse en contacto con nosotros y otros desarrolladores de Visual Studio a través de nuestra [conversación de Visual Studio en la comunidad de Gitter](https://gitter.im/Microsoft/VisualStudio).  (Esta opción requiere una cuenta de [GitHub](https://github.com/)).

## <a name="see-also"></a>Vea también
* [Instalación de Visual Studio 2017](install-visual-studio.md)
* [Actualizar Visual Studio 2017](update-visual-studio.md)
* [Modificación de Visual Studio 2017](modify-visual-studio.md)
* [Desinstalación de Visual Studio 2017](uninstall-visual-studio.md)
