---
title: Instalación de Visual Studio 2017 | Microsoft Docs
description: Obtenga información sobre cómo instalar Visual Studio, paso a paso.
ms.custom: ''
ms.date: 05/07/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio
- dev15
- set up Visual Studio
- Visual Studio setup
- Visual Studio installer
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6eba5c5dc2ec357d9aaf6a5e8f9cdef18102b8da
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49856176"
---
# <a name="install-visual-studio-2017"></a>Instalación de Visual Studio 2017

Le presentamos una nueva manera de instalar Visual Studio. En nuestra versión más reciente, hemos facilitado la selección e instalación de solo las características que necesita. También hemos reducido el espacio de Visual Studio al mínimo, de manera que se instale más rápidamente con menos impacto del sistema que nunca antes.

¿Quiere saber más sobre otras novedades de esta versión? Vea nuestras [notas de la versión](/visualstudio/releasenotes/vs2017-relnotes).

¿Está listo para instalarlo? Le guiaremos paso a paso.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Paso 1: Asegurarse de que el equipo está listo para Visual Studio

Antes de comenzar la instalación de Visual Studio:

1. Compruebe los [requisitos del sistema](/visualstudio/productinfo/vs2017-system-requirements-vs). Estos requisitos le permiten saber si el equipo es compatible con Visual Studio 2017.
2. Aplique las actualizaciones de Windows más recientes. Estas actualizaciones garantizan que el equipo tiene las actualizaciones de seguridad más recientes y los componentes del sistema necesarios para Visual Studio.
3. Reinicie el equipo. El reinicio garantiza que cualquier actualización o instalación pendiente no dificultará la instalación de Visual Studio.
4. Libere espacio. Quite los archivos y aplicaciones innecesarios de %SystemDrive% ejecutando, por ejemplo, la aplicación Liberar espacio.

Si tiene preguntas sobre cómo ejecutar las versiones anteriores de Visual Studio en paralelo con Visual Studio 2017, vea los [detalles de compatibilidad con Visual Studio](/visualstudio/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases).

## <a name="step-2---download-visual-studio"></a>Paso2: Descargar Visual Studio

A continuación, descargue el archivo de programa previo de Visual Studio. Para ello, haga clic en el botón siguiente, seleccione la edición de Visual Studio 2017 que desee instalar, haga clic en **Guardar** y, a continuación, haga clic en **Abrir carpeta**.

 > [!div class="button"]
 > [Descargar Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
<br/>

|         |         |
|---------|---------|
|  ![icono de cámara de película para vídeo](media/video-icon.png "Ver un vídeo")  |    [Vea un vídeo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Download-the-Visual-Studio-Installer-GgrESHD6D_3311787171) sobre cómo descargar el archivo del programa previo de Visual Studio y seleccione la edición de Visual Studio que sea más adecuada. |

## <a name="step-3---install-the-visual-studio-installer"></a>Paso 3: Desinstalar el Instalador de Visual Studio

Después, ejecute el archivo de programa previo para instalar el Instalador de Visual Studio. Este nuevo instalador ligero incluye todo lo necesario para instalar y personalizar Visual Studio 2017.

1. Desde la carpeta **Descargas**, haga doble clic en el archivo de programa previo que coincida o sea similar a uno de los siguientes archivos:

   * **vs_enterprise.exe** para Visual Studio Enterprise
   * **vs_professional.exe** para Visual Studio Professional
   * **vs_community.exe** para Visual Studio Community  <br><br>

   Si recibe un aviso de Control de cuentas de usuario, haga clic en **Sí**.

2. Le pediremos que acepte los [Términos de licencia](https://visualstudio.microsoft.com/license-terms/) de Microsoft y la [Declaración de privacidad](https://privacy.microsoft.com/privacystatement) de Microsoft. Haga clic en **Continuar**.

   ![Términos de licencia y declaración de privacidad](media/vs2017-privacy-and-license-terms.PNG "Términos de licencia y declaración de privacidad de Microsoft")

## <a name="step-4---select-workloads"></a>Paso 4: Seleccionar cargas de trabajo

Una vez instalado el Instalador, puede usarlo para personalizar la instalación mediante la selección de los conjuntos de características, o cargas de trabajo, que desee. Esta es la manera de hacerlo.

1. Busque la carga de trabajo que quiera en la pantalla **Instalando Visual Studio**.

   ![Seleccionar una carga de trabajo en el cuadro de diálogo del programa de instalación de Visual Studio 2017](../install/media/install-visual-studio-community.png)

     Por ejemplo, elija la carga de trabajo "Desarrollo de escritorio de .NET". Incluye el editor principal predeterminado, que contiene compatibilidad de edición de código básica para más de 20 lenguajes, la capacidad de abrir y editar código desde cualquier carpeta sin necesitar un proyecto y control de código fuente integrado.

2. Después de que seleccione las cargas de trabajo que quiera, haga clic en **Instalar**.

    Después, aparecerán las pantallas de estado que muestran el progreso de su instalación de Visual Studio.

3. Después de que se instalen los nuevos componentes y cargas de trabajo, haga clic en **Iniciar**.

> [!TIP]
> En cualquier momento después de la instalación, puede instalar las cargas de trabajo o los componentes que no instaló inicialmente. Si tiene Visual Studio abierto, vaya a **Herramientas** > **Obtener herramientas y características...** para abrir el Instalador de Visual Studio. O bien, abra el **Instalador de Visual Studio** desde el menú Inicio. Desde allí, puede seleccionar las cargas de trabajo o los componentes que quiere instalar, y después, haga clic en **Modificar**.

|         |         |
|---------|---------|
|  ![icono de cámara de película para vídeo](media/video-icon.png "Ver un vídeo")  |    [Vea un vídeo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Workloads-in-Visual-Studio-2017-jHE19HD6D_1611787171) sobre cómo instalar el Instalador de Visual Studio e instalar después una carga de trabajo. |

## <a name="step-5---select-individual-components-optional"></a>Paso 5: Seleccionar componentes individuales (opcional)

Si no desea usar la característica Cargas de trabajo para personalizar la instalación de Visual Studio, puede hacerlo mediante la instalación de componentes individuales. Para seleccionar componentes individuales, haga clic en la opción **Componentes individuales** del Instalador de Visual Studio, seleccione lo que quiera y siga las indicaciones.

  ![Visual Studio 2017 - Instalar componentes individuales](media/vs2017-components.PNG "Instalar componentes individuales de Visual Studio")

  |         |         |
  |---------|---------|
  |  ![icono de cámara de película para vídeo](media/video-icon.png "Ver un vídeo")  |   [Vea un vídeo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Components-in-Visual-Studio-2017-ZMfaVID6D_7411787171) sobre cómo instalar un componente individual con el Instalador de Visual Studio. |

## <a name="step-6---install-language-packs-optional"></a>Paso 6 - Instalar paquetes de idioma (opcional)

De manera predeterminada, el programa instalador intenta hacer coincidir el idioma del sistema operativo cuando se ejecuta por primera vez. Para instalar Visual Studio 2017 en un idioma de su elección, haga clic en la opción **Paquetes de idioma** del instalador de Visual Studio y siga las indicaciones.

  ![Visual Studio 2017 - Instalar paquetes de idioma](media/vs2017-languages.PNG "Instalar paquetes de idioma de Visual Studio")

  |         |         |
  |---------|---------|
  |  ![icono de cámara de película para vídeo](media/video-icon.png "Ver un vídeo")  |   [Vea un vídeo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Language-Packs-in-Visual-Studio-2017-ByT7yID6D_9011787171) sobre cómo instalar un paquete de idioma con el Instalador de Visual Studio. |

### <a name="change-the-installer-language-from-the-command-line"></a>Cambio del idioma del instalador en la línea de comandos

Otra manera de cambiar el idioma predeterminado es mediante la ejecución del instalador desde la línea de comandos. Por ejemplo, puede forzar al instalador a utilizar el inglés utilizando el comando siguiente: `vs_installer.exe --locale en-US`. El instalador recordará esta configuración cuando se ejecute la próxima vez. El instalador admite los siguientes tokens de idioma: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru y tr-tr.

## <a name="step-7---change-the-installation-location-optional"></a>Paso 7: Cambiar la ubicación de instalación (opcional)

**Nuevo en 15.7**: ahora puede reducir el tamaño de instalación de Visual Studio en la unidad de sistema. Puede mover la caché de descarga, los componentes compartidos, SDK y herramientas a distintas unidades y mantener Visual Studio en la unidad que lo ejecuta más rápido.

  ![Visual Studio 2017: cambiar la ubicación de instalación](media/installation-options-by-location.png "Change the installation location")

Para obtener más información, consulte la página [Change installation locations in Visual Studio](change-installation-locations.md) (Cambiar las ubicaciones de instalación de Visual Studio).

## <a name="step-8---start-developing"></a>Paso 8: Empezar a desarrollar

1. Una vez completada la instalación de Visual Studio, haga clic en el botón **Iniciar** para empezar a desarrollar con Visual Studio.

2. Haga clic en **Archivo** y después en **Nuevo proyecto**.

3. Seleccione un tipo de proyecto.

   Por ejemplo, para [compilar una aplicación de C++](../ide/getting-started-with-cpp-in-visual-studio.md), haga clic en **Instalado**, expanda **Visual C++** y, después, seleccione el tipo de proyecto de C++ que quiera compilar.

   Para [compilar una aplicación de C#](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md), haga clic en **Instalado**, expanda **Visual C#** y, después, seleccione el tipo de proyecto de C# que quiera compilar.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Actualizar Visual Studio 2017](update-visual-studio.md)
* [Modificación de Visual Studio 2017](modify-visual-studio.md)
* [Desinstalación de Visual Studio 2017](uninstall-visual-studio.md)
* [Crear una instalación sin conexión de Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
* [Configuración e instalación de Visual Studio para Mac](/visualstudio/mac/installation)