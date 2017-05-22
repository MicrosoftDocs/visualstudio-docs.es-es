---
title: "Actualización de una instalación basada en red de Visual Studio | Microsoft Docs"
description: "{{MARCADOR DE POSICIÓN}}"
ms.date: 05/05/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: timsneath
ms.author: tims
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
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 75c65d75ab751058ac435d62f253ead149ccfe42
ms.contentlocale: es-es
ms.lasthandoff: 05/09/2017

---
# <a name="update-a-network-based-installation-of-visual-studio"></a>Actualización de una instalación basada en red de Visual Studio

Se puede actualizar un diseño de instalación de red de Visual Studio con las actualizaciones de producto más recientes, de forma que se puede usar tanto como punto de instalación de la actualización más reciente de Visual Studio como para mantener instalaciones que ya están implementadas en estaciones de trabajo cliente.

## <a name="how-to-update-a-network-layout"></a>Actualización de un diseño de red
Para actualizar el recurso compartido de instalación de red para que incluya las actualizaciones más recientes, ejecute el mismo comando `--layout` que ejecutó cuando se creó inicialmente el diseño para descargar paquetes actualizados de forma incremental.

Si seleccionó un diseño parcial cuando creó por primera vez el diseño de red, asegúrese de usar los mismos parámetros de línea de comandos que esta primera vez (es decir, las mismas cargas de trabajo y lenguajes). Si elige opciones diferentes, el segundo comando `--layout` no actualizará los paquetes que no se especificaron la segunda vez.

Si hospeda un diseño en un recurso compartido de archivos, se recomienda que actualice una copia privada del diseño (por ejemplo, `c:\vs2017offline`) y, después de descargar todo el contenido actualizado, lo copie en dicho recurso compartido de archivos (por ejemplo, `\\server\products\VS2017`).  Si no lo hace, existe una mayor probabilidad de que los usuarios que ejecutan el programa de instalación mientras se actualiza el diseño no puedan obtener todo el contenido del diseño ya que no está completamente actualizado.

## <a name="how-to-deploy-an-update-to-client-machines"></a>Implementación de una actualización en máquinas cliente
En función de cómo esté configurado el entorno de red, una actualización puede ser implementada por un administrador de empresa o se puede iniciar desde una máquina cliente. 

- Los usuarios pueden actualizar una instancia de Visual Studio que se instaló desde una carpeta de instalación sin conexión:
  - Ejecute el instalador de Visual Studio.
  - Haga clic en **Actualizar**.

- Los administradores pueden actualizar las implementaciones de cliente de Visual Studio sin interacción del usuario con dos comandos independientes:
  - En primer lugar, actualice el instalador de Visual Studio: <br>```vs_enterprise.exe --quiet --update```
  - Luego, actualice la propia aplicación de Visual Studio: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

> [!NOTE]
> Use el comando [vswhere.exe](tools-for-managing-visual-studio-instances.md) para identificar la ruta de instalación de una instancia existente de Visual Studio en una máquina cliente.

> [!TIP]
> Para más información sobre cómo controlar cuándo se presentan notificaciones de actualización a los usuarios, consulte [Control updates to network-based Visual Studio deployments](controlling-updates-to-visual-studio-deployments.md) (Control de actualizaciones a implementaciones de Visual Studio basadas en red).


## <a name="see-also"></a>Vea también
* [Instalar Visual Studio](install-visual-studio.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Herramientas para detectar y administrar instancias de Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Control updates to network-based Visual Studio deployments](controlling-updates-to-visual-studio-deployments.md) (Control de actualizaciones de implementaciones de Visual Studio basadas en red)

