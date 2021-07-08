---
title: Quitar Visual Studio
titleSuffix: ''
description: Obtenga información sobre cómo quitar completamente Visual Studio del equipo, paso a paso.
ms.date: 12/19/2019
ms.custom: seodec18
ms.topic: how-to
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
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 5af0cf31d3a53b12910ea8108c93a99cbaf3e87f
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306961"
---
# <a name="remove-visual-studio"></a>Quitar Visual Studio

Si se produce un error grave y Visual Studio no se puede reparar o desinstalar, puede ejecutar la herramienta `InstallCleanup.exe` para quitar los archivos de instalación y la información de producto de todas las instancias instaladas de Visual Studio 2017, Visual Studio 2019 o Visual Studio 2022.

> [!WARNING]
> Use la herramienta InstallCleanup **solo como último recurso** si se produce un error en la reparación o la desinstalación. Esta herramienta podría desinstalar características de otras instalaciones de Visual Studio u otros productos, que en ese caso es posible que también necesiten repararse o volver a instalarse.

## <a name="run-installcleanupexe"></a>Ejecución de InstallCleanup.exe

Puede usar cualquiera de los siguientes modificadores de la línea de comandos con la herramienta `InstallCleanup.exe`:

| Modificador | Comportamiento                                                                                                                                                                                                                                                                                                                 |
|--------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-i`   | Este modificador es el predeterminado si no se pasa ningún otro. Quita solo el directorio de instalación principal y la información de producto. Use este modificador si piensa volver a instalar la misma versión de Visual Studio después de ejecutar la herramienta `InstallCleanup.exe`.                                                              |
| `-f`   | Este modificador quita el directorio de instalación principal, la información de producto y la mayoría de las demás características instaladas fuera del directorio de instalación, que también pueden estar compartidas con otras instalaciones de Visual Studio u otros productos. Use este modificador si piensa quitar Visual Studio sin volverlo a instalar más adelante. |

Aquí se muestra cómo ejecutar la herramienta `InstallCleanup.exe`:

1. Cierre el instalador de Visual Studio.
1. Abra un símbolo del sistema de administrador. Para abrir un símbolo del sistema de administrador, siga estos pasos:
   * Escriba **cmd** en el cuadro "Escriba aquí para ejecutar la búsqueda".
   * Haga clic con el botón derecho en **Símbolo del sistema** y luego elija **Ejecutar como administrador**.
1. Escriba la ruta de acceso completa de la herramienta `InstallCleanup.exe` y agregue el modificador de la línea de comandos que prefiera. De forma predeterminada, la ruta de acceso de la herramienta es como la que se indica a continuación. Las comillas dobles incluyen un comando que contiene espacios:

   ```shell
   "C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe"
   ```

   > [!NOTE]
   > Si no encuentra `InstallCleanup.exe` en el directorio del instalador de Visual Studio, que siempre se encuentra en `%ProgramFiles(x86)%\Microsoft Visual Studio`, esto es lo que se debe hacer a continuación. Siga las instrucciones para [instalar Visual Studio](install-visual-studio.md). A continuación, cuando se muestre la pantalla de selección de cargas de trabajo, cierre la ventana y siga los pasos que aparecen en esta página de nuevo.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Instalar Visual Studio](install-visual-studio.md)
* [Actualizar Visual Studio](update-visual-studio.md)
* [Modificar Visual Studio](modify-visual-studio.md)
* [Desinstalar Visual Studio](uninstall-visual-studio.md)
