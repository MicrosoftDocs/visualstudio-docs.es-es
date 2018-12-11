---
title: Instalación de una versión preliminar
description: Instrucciones para actualizar Visual Studio para Mac y acceder a versiones preliminares, incluidas las versiones preliminares de Visual Studio 2019 para Mac.
zone_pivot_groups: mac-ide-version
author: conceptdev
ms.author: crdun
ms.date: 11/03/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 0E1EF257-9DE4-4653-9DF4-805CE007A1A1
ms.openlocfilehash: b5eea8c2c894b7eeaa13c83ae6698d1297de9297
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896762"
---
# <a name="install-a-preview-release"></a>Instalación de una versión preliminar

::: zone pivot="vsmac2019"

> [!TIP]
> Ya está disponible la versión preliminar de Visual Studio 2019 para Mac. Por primera vez, se puede instalar junto con la última versión estable de Visual Studio para Mac.

## <a name="requirements-for-the-visual-studio-2019-for-mac-preview"></a>Requisitos de la versión preliminar de Visual Studio 2019 para Mac

* Equipo Mac con macOS High Sierra 10.13 o una versión posterior.

Para compilar aplicaciones Xamarin para iOS o macOS, también necesitará lo siguiente:

* Xcode 10.0 o una versión posterior. Por lo general, se recomienda usar la versión estable más reciente.
* Un ID de Apple. Si aún no tiene un ID de Apple, puede crearlo en https://appleid.apple.com. Es necesario tener un ID de Apple para la instalación y el inicio de sesión en Xcode.

## <a name="installing-the-preview"></a>Instalación de la versión preliminar

1. Descargue el instalador en la [página de la versión preliminar de Visual Studio para Mac](https://aka.ms/vs4mac-preview).
2. Una vez completada la descarga, haga clic en **VisualStudioforMacPreviewInstaller.dmg** para montar el instalador y ejecútelo haciendo doble clic en el logotipo de flecha:

    [![Haga clic en la flecha grande para comenzar la instalación.](media/install-preview-installer-sml.png)](media/install-preview-installer.png#lightbox)

3. Es posible que se muestre una advertencia en la que se indique que la aplicación se ha descargado de Internet. Haga clic en **Abrir**.
4. Espere mientras el programa de instalación comprueba el sistema:

    [![El instalador comprueba si los componentes están instalados en el sistema.](media/install-preview-checking-sml.png)](media/install-preview-checking.png#lightbox)

5. Se mostrará una alerta en la que se le solicitará que acepte los términos de licencia y de privacidad. Haga clic en los vínculos para leerlos y, si está de acuerdo, presione **Continuar**:

    [![Haga clic en los vínculos a los términos de licencia y privacidad y, si está de acuerdo, continúe.](media/install-preview-privacy-sml.png)](media/install-preview-privacy.png#lightbox)

6. Se mostrará una lista de las cargas de trabajo disponibles. Seleccione las que quiera usar:

    [![Elija las características de carga de trabajo opcionales que quiera instalar.](media/install-preview-selection-sml.png)](media/install-preview-selection.png#lightbox)

    Si la versión actual de Visual Studio para Mac 2017 es anterior a la 7.7, se le solicitará que apruebe una actualización a la última versión estable, lo cual es necesario para poder realizar la instalación en paralelo. Presione **Continuar** para aprobar la actualización:

    ![Es necesario efectuar la actualización a la versión estable 7.7.](media/install-preview-older-upgrade.png)

7. Después de haber realizado las selecciones, presione el botón **Instalar**.
8. El instalador mostrará el progreso a medida que se realiza la descarga y la instalación de Visual Studio para Mac, así como de las cargas de trabajo seleccionadas. Es posible que se le solicite que indique la contraseña para conceder los privilegios necesarios para la instalación.
9. Use **Visual Studio (versión preliminar)** siempre que quiera probar dicha versión preliminar o use la última versión estable para realizar trabajos de producción. Aquí se muestran los dos iconos:

    ![Diferencias entre los iconos de la versión estable y la preliminar](media/install-preview-icons-sml.png)

Si tiene problemas de red al instalar un entorno corporativo, revise las instrucciones de [instalación tras un firewall o proxy](https://docs.microsoft.com/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server).

Obtenga más información sobre los cambios en las [notas de la versión](https://docs.microsoft.com/visualstudio/releasenotes/vs2019-mac-preview-relnotes).

::: zone-end
::: zone pivot="vsmac2017"

## <a name="install-an-update-for-visual-studio-2017-for-mac"></a>Instalación de una actualización para Visual Studio 2017 para Mac

Antes de lanzar oficialmente una nueva versión de Visual Studio para Mac, está disponible como versión preliminar. La versión preliminar le da la oportunidad de probar las nuevas características y obtener las últimas correcciones de errores antes de que se incorporen completamente al producto.

Las versiones preliminares de Visual Studio para Mac se distribuyen como actualizaciones, y no mediante una descarga aparte. Visual Studio para Mac tiene tres canales de actualización, que se describen en el artículo de [actualización](update.md): Stable, Beta y Alpha.

La mayoría de las versiones preliminares estarán disponibles a través de los canales **Beta** y **Alpha**, pero consulte siempre las [Notas de la versión preliminar](/visualstudio/releasenotes/vs2017-mac-preview-relnotes) para obtener información más precisa.

Para instalar la versión preliminar de Visual Studio para Mac, siga estos pasos:

1. Vaya a **Visual Studio > Buscar actualizaciones**.
2. En el cuadro combinado de canales de actualización, seleccione **Beta**.
3. Seleccione el botón **Switch channel** (Conmutador de canal) para cambiar al canal seleccionado e iniciar la descarga de nuevas actualizaciones.
4. Seleccione el botón **Reiniciar e instalar actualizaciones** para iniciar la instalación de actualizaciones.

Para obtener más información sobre las actualizaciones de Visual Studio para Mac, vea el artículo sobre [actualización](update.md).

::: zone-end