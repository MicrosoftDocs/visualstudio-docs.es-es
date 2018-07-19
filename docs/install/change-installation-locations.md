---
title: Cambio de las ubicaciones de instalación en Visual Studio 2017
description: Aprenda a reducir la huella de instalación en la unidad del sistema cambiando la ubicación de la caché de descarga, los componentes compartidos, SDK y algunas herramientas a distintas unidades.
ms.date: 05/07/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- change installation locations for Visual Studio
- move installation files to different drives
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a6d8741982efd5329e7c14f0a32fb66bbdd377f5
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/20/2018
ms.locfileid: "36282065"
---
# <a name="change-the-installation-locations-in-visual-studio-2017"></a>Cambio de las ubicaciones de instalación en Visual Studio 2017

**Novedad en 15.7**: Puede reducir la huella de instalación en la unidad del sistema trasladando la caché de descarga, los componentes compartidos, SDK y algunas herramientas a distintas unidades.

Esta es la manera de hacerlo.

1. Cuando instale Visual Studio, elija la pestaña **Opciones de instalación**.

  ![Visual Studio 2017: cambiar la ubicación de instalación](media/installation-options-by-location.png "Change the installation location")

  > [!IMPORTANT]
  > Si pausa la instalación y la reanuda más tarde, Visual Studio la retoma donde se quedó. En otras palabras, el progreso se aplica a lo que queda por descargar e instalar, en lugar de empezar desde el recuento anterior.

2. En la sección **IDE de Visual Studio**, acepte el valor predeterminado. Esto instala el producto principal e incluye los archivos que son específicos para esta versión de Visual Studio.

 > [!IMPORTANT]
 > Si la unidad del sistema es una unidad de estado sólido (SSD),el motivo por el que se recomienda que acepte la ubicación predeterminada en la unidad del sistema es el siguiente: cuando desarrolla con Visual Studio, lee y escribe en una gran cantidad de archivos, lo que aumenta la actividad de E/S del disco.  Es mejor que elija la unidad más rápida para que administre la carga.

2. En la sección **Caché de descarga**, decida si quiere mantener la caché de descarga y, después, active o desactive **Mantener la caché de descarga** en consecuencia. <br><br>Si decide no mantener la caché de descarga, la ubicación solo se usará de forma temporal. Además, esta acción no afecta ni elimina los archivos de las instalaciones anteriores. (Para limpiar todos los paquetes de instalación debe modificar las instalaciones anteriores por separado).

3. En la sección **Caché de descarga**, especifique la unidad donde quiere almacenar los archivos de instalación y los manifiestos. <br><br>Por ejemplo, si selecciona la carga de trabajo “Desarrollo para el escritorio con C++”, el tamaño necesario temporalmente es de 1,58 GB en la unidad del sistema, que se liberará en cuanto finalice la instalación.

 > [!NOTE]
 > Los archivos primero se descargan en una carpeta temporal en la unidad del sistema y luego se eliminan, después de que Visual Studio los compruebe y luego los mueva a la carpeta de caché de descarga. Si opta por mantener la caché de descarga en una unidad diferente, Visual Studio todavía un necesitará espacio en disco equivalente al tamaño de la caché de descarga en la unidad del sistema.
 > [!IMPORTANT]
 > La ubicación se establece con la primera instalación y no se puede cambiar más adelante desde el instalador de la interfaz de usuario. En su lugar, debe [usar parámetros de línea de comandos](use-command-line-parameters-to-install-visual-studio.md) para mover la caché de descarga

4. En la sección **Componentes, herramientas y SDK compartidos**, especifique la unidad donde quiere almacenar los archivos que se comparten entre las instalaciones de Visual Studio en paralelo. Los SDK y las herramientas que permiten que el instalador de Visual Studio cambie su ubicación de instalación también se almacenan en este directorio.

 > [!NOTE]
 > Hay algunas herramientas y SDK que tiene sus propias reglas sobre dónde se pueden instalar. Estas herramientas y SDK todavía se instalarán en la unidad del sistema incluso si elige otra ubicación).

## <a name="get-support"></a>Obtener soporte técnico

En ocasiones, algo no sale según lo previsto. Si se produce un error en la instalación de Visual Studio, consulte la página [Troubleshooting Visual Studio 2017 installation and upgrade issues](troubleshooting-installation-issues.md) (Solucionar problemas de errores de instalación y actualización de Visual Studio 2017) para obtener ayuda. También puede ponerse en contacto con nosotros para obtener ayuda sobre la instalación por [chat en directo](https://visualstudio.microsoft.com/vs/support/#talktous) (solo en inglés); para obtener más información, consulte la [página "Póngase en contacto con nosotros" de Visual Studio](https://visualstudio.microsoft.com/vs/support/#talktous).

Aquí tiene algunas opciones de soporte técnico más:

* Puede notificarnos problemas del producto a través de la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) que aparece en el instalador y en el IDE de Visual Studio.
* Puede compartir una sugerencia de producto con nosotros en [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Puede realizar el seguimiento de los problemas del producto y encontrar respuestas en la [comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/).
* También puede ponerse en contacto con nosotros y otros desarrolladores de Visual Studio a través de la [conversación de Visual Studio en la comunidad de Gitter](https://gitter.im/Microsoft/VisualStudio). (Esta opción requiere una cuenta de [GitHub](https://github.com/)).

## <a name="see-also"></a>Vea también

* [Instalación de Visual Studio 2017](install-visual-studio.md)
* [Actualizar Visual Studio 2017](update-visual-studio.md)
* [Modificación de Visual Studio 2017](update-visual-studio.md)
* [Desinstalación de Visual Studio 2017](uninstall-visual-studio.md)
