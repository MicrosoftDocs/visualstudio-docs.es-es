---
title: Problemas conocidos de contenedores | Microsoft Docs
ms.custom: 
ms.date: 10/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: heaths
ms.author: heaths
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6edcc59a2d726fbd76fee86b750f21dc468b727e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="known-issues-for-containers"></a>Problemas conocidos de contenedores

Hay algunos problemas al instalar Visual Studio en un contenedor Docker.

## <a name="windows-container"></a>Contenedor de Windows

Los problemas conocidos aquí descritos se producen cuando se instala Visual Studio Build Tools 2017 en un contenedor de Windows.

* No se puede instalar Visual Studio en un contenedor basado en la imagen microsoft/windowsservercore:10.0.14393.1593. Las imágenes etiquetadas con versiones anteriores o más recientes de Windows deberían funcionar.
* No se pueden instalar versiones del SDK de Windows anteriores a 10.0.14393. Algunos paquetes no se pueden instalar y las cargas de trabajo que dependen de esos paquetes no funcionarán.
* Debe pasar `-m 2GB` (o más) al compilar la imagen. Algunas cargas de trabajo requieren más memoria de la predeterminada (1 GB) cuando se instalan.
* Debe configurar Docker para usar discos mayores que el valor predeterminado de 20 GB.
* Debe pasar `--norestart` en la línea de comandos. Al redactar este artículo, el intento de reinicio de un contenedor de Windows desde el contenedor devuelve `ERROR_TOO_MANY_OPEN_FILES` al host.

## <a name="build-tools-container"></a>Contenedor de Build Tools

Es posible que se produzcan los siguientes problemas conocidos al usar un contenedor de Build Tools. Para ver si se han corregido problemas o si hay otros problemas conocidos, visite https://developercommunity.visualstudio.com.

* Es posible que IntelliTrace no funcione en [algunos escenarios](https://github.com/Microsoft/vstest/issues/940) dentro de un contenedor.

## <a name="get-support"></a>Obtener soporte técnico
En ocasiones, algo no sale según lo previsto. Si se produce un error en la instalación de Visual Studio, consulte la página [Troubleshooting Visual Studio 2017 installation and upgrade issues](troubleshooting-installation-issues.md) (Solucionar problemas de errores de instalación y actualización de Visual Studio 2017). Si ninguno de los pasos de solución de problemas ayuda, puede ponerse en contacto con nosotros por chat para obtener asistencia para la instalación (solo en inglés). Para más información, consulte la [página de soporte técnico de Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Aquí tiene algunas opciones de soporte técnico más:
* Puede notificarnos problemas del producto a través de la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) que aparece en el instalador y en el IDE de Visual Studio.
* Puede compartir una sugerencia de producto con nosotros en [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Puede realizar el seguimiento de los problemas del producto en la [comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/), y hacer preguntas y encontrar respuestas.
* También puede ponerse en contacto con nosotros y otros desarrolladores de Visual Studio a través de nuestra [conversación de Visual Studio en la comunidad de Gitter](https://gitter.im/Microsoft/VisualStudio).  (Esta opción requiere una cuenta de [GitHub](https://github.com/)).

## <a name="see-also"></a>Vea también

* [Instalar Build Tools en un contenedor](build-tools-container.md)
* [Ejemplo avanzado de contenedores](advanced-build-tools-container.md)
* [Identificadores de componentes y cargas de trabajo de Visual Studio Build Tools 2017](workload-component-id-vs-build-tools.md)
