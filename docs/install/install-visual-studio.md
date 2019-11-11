---
title: Instalar Visual Studio
titleSuffix: ''
description: Obtenga información sobre cómo instalar Visual Studio, paso a paso.
ms.date: 10/07/2019
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 6cd91fadea397955b756461383ed8e17030b4c3b
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018855"
---
# <a name="install-visual-studio"></a>Instalar Visual Studio

::: moniker range="vs-2019"

Bienvenido a Visual Studio 2019. En esta versión, resulta muy fácil elegir e instalar solo las características que se necesitan. Además, gracias a la mínima superficie de memoria que ocupa, se instala rápidamente y con menos impacto en el sistema.

::: moniker-end

::: moniker range="vs-2017"

Le presentamos una nueva manera de instalar Visual Studio. En esta versión, resulta muy fácil elegir e instalar solo las características que se necesitan. También hemos reducido el espacio de Visual Studio al mínimo, de manera que se instale más rápidamente con menos impacto del sistema que nunca antes.

::: moniker-end

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Instalación de Visual Studio para Mac](/visualstudio/mac/installation/).

::: moniker range="vs-2019"

¿Quiere saber más sobre otras novedades de esta versión? Vea nuestras [notas de la versión](/visualstudio/releases/2019/release-notes/).

::: moniker-end

::: moniker range="vs-2017"

¿Quiere saber más sobre otras novedades de esta versión? Vea nuestras [notas de la versión](/visualstudio/releasenotes/vs2017-relnotes).

::: moniker-end

¿Está listo para instalarlo? Le guiaremos paso a paso.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Paso 1: Asegurarse de que el equipo está listo para Visual Studio

Antes de comenzar la instalación de Visual Studio:

::: moniker range="vs-2017"

1. Compruebe los [requisitos del sistema](/visualstudio/productinfo/vs2017-system-requirements-vs). Estos requisitos le permiten saber si el equipo es compatible con Visual Studio 2017.

1. Aplique las actualizaciones de Windows más recientes. Estas actualizaciones garantizan que el equipo tiene las actualizaciones de seguridad más recientes y los componentes del sistema necesarios para Visual Studio.

1. Reinicie el equipo. El reinicio garantiza que cualquier actualización o instalación pendiente no dificultará la instalación de Visual Studio.

1. Libere espacio. Quite los archivos y aplicaciones innecesarios de %SystemDrive% ejecutando, por ejemplo, la aplicación Liberar espacio.

::: moniker-end

::: moniker range="vs-2019"

1. Compruebe los [requisitos del sistema](/visualstudio/releases/2019/system-requirements). Estos requisitos le permiten saber si el equipo es compatible con Visual Studio 2019.

1. Aplique las actualizaciones de Windows más recientes. Estas actualizaciones garantizan que el equipo tiene las actualizaciones de seguridad más recientes y los componentes del sistema necesarios para Visual Studio.

1. Reinicie el equipo. El reinicio garantiza que cualquier actualización o instalación pendiente no dificultará la instalación de Visual Studio.

1. Libere espacio. Quite los archivos y aplicaciones innecesarios de %SystemDrive% ejecutando, por ejemplo, la aplicación Liberar espacio.

::: moniker-end

::: moniker range="vs-2017"

Si tiene preguntas sobre cómo ejecutar las versiones anteriores de Visual Studio en paralelo con Visual Studio 2017, vea los [detalles de compatibilidad con Visual Studio](/visualstudio/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases).

::: moniker-end

::: moniker range="vs-2019"

Si tiene dudas sobre cómo ejecutar versiones anteriores de Visual Studio en paralelo con Visual Studio 2019, vea la página [Compatibilidad y destinatarios de la plataforma de Visual Studio 2019](/visualstudio/releases/2019/compatibility/).

::: moniker-end

## <a name="step-2---download-visual-studio"></a>Paso2: Descargar Visual Studio

A continuación, descargue el archivo de programa previo de Visual Studio.

::: moniker range="vs-2017"

Para obtener un programa previo de Visual Studio 2017, consulte la página de descarga de [versiones anteriores de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) y obtenga información detallada sobre cómo hacerlo.

::: moniker-end

::: moniker range="vs-2019"

Para ello, elija el siguiente botón, la edición de Visual Studio que quiera instalar, **Guardar** y, por último, **Abrir carpeta**.

 > [!div class="button"]
 > [Descarga de Visual Studio](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="step-3---install-the-visual-studio-installer"></a>Paso 3: Instalar el Instalador de Visual Studio

Ejecute el archivo de programa previo para instalar el Instalador de Visual Studio. Este nuevo instalador ligero incluye todo lo necesario para instalar y personalizar Visual Studio.

1. Desde la carpeta **Descargas**, haga doble clic en el archivo de programa previo que coincida o sea similar a uno de los siguientes archivos:

   * **vs_community.exe** para Visual Studio Community
   * **vs_professional.exe** para Visual Studio Professional
   * **vs_enterprise.exe** para Visual Studio Enterprise

   Si recibe un aviso de Control de cuentas de usuario, elija **Sí**.

2. Le pediremos que acepte los [Términos de licencia](https://visualstudio.microsoft.com/license-terms/) de Microsoft y la [Declaración de privacidad](https://privacy.microsoft.com/privacystatement) de Microsoft. Elija **Continuar**.

   ![Términos de licencia y declaración de privacidad](media/privacy-and-license-terms.png "Términos de licencia y declaración de privacidad de Microsoft")

## <a name="step-4---choose-workloads"></a>Paso 4: Elección de las cargas de trabajo

Una vez instalado el Instalador, puede usarlo para personalizar la instalación mediante la selección de los conjuntos de características, o cargas de trabajo, que desee. Esta es la manera de hacerlo.

 ::: moniker range="vs-2017"

1. Busque la carga de trabajo que quiera en la pantalla **Instalando Visual Studio**.

   ![Visual Studio 2017: Instalación de una carga de trabajo](../install/media/vs-installer-installing-workloads.png)

     Por ejemplo, elija la carga de trabajo "Desarrollo de escritorio de .NET". Incluye el editor principal predeterminado, que contiene compatibilidad de edición de código básica para más de 20 lenguajes, la capacidad de abrir y editar código desde cualquier carpeta sin necesitar un proyecto y control de código fuente integrado.

1. Después de elegir las cargas de trabajo que quiera, haga clic en **Instalar**.

    Después, aparecerán las pantallas de estado que muestran el progreso de su instalación de Visual Studio.

 ::: moniker-end

::: moniker range="vs-2019"

1. Después de que se instalen los nuevos componentes y cargas de trabajo, elija **Iniciar**.

   ![Visual Studio 2019: Instalación de una carga de trabajo](../install/media/vs-2019/vs-installer-workloads.png)

     Por ejemplo, elija la carga de trabajo "Desarrollo de ASP.NET y web". Incluye el editor principal predeterminado, que contiene compatibilidad de edición de código básica para más de 20 lenguajes, la capacidad de abrir y editar código desde cualquier carpeta sin necesitar un proyecto y control de código fuente integrado.

1. Después de elegir las cargas de trabajo que quiera, haga clic en **Instalar**.

    Después, aparecerán las pantallas de estado que muestran el progreso de su instalación de Visual Studio.

 ::: moniker-end

> [!TIP]
> En cualquier momento después de la instalación, puede instalar las cargas de trabajo o los componentes que no instaló inicialmente. Si tiene Visual Studio abierto, vaya a **Herramientas** > **Obtener herramientas y características...** para abrir el Instalador de Visual Studio. O bien, abra el **Instalador de Visual Studio** desde el menú Inicio. A partir de ahí, puede elegir las cargas de trabajo o los componentes que quiera instalar. A continuación, elija **Modificar**.

## <a name="step-5---choose-individual-components-optional"></a>Paso 5: Selección de componentes individuales (opcional)

Si no quiere usar la característica Cargas de trabajo para personalizar la instalación de Visual Studio o quiere agregar más componentes de los que instala una carga de trabajo, puede hacerlo instalando o agregando componentes individuales desde la pestaña **Componentes individuales**. Elija los elementos que quiera y, luego, siga las indicaciones.

::: moniker range="vs-2017"

  ![Visual Studio 2017 - Instalar componentes individuales](media/vs-installer-installing-components.png "Instalar componentes individuales de Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

  ![Visual Studio 2019: Instalación de componentes individuales](media/vs-2019/vs-installer-individual-components.png "Instalación de componentes individuales de Visual Studio")

::: moniker-end

## <a name="step-6---install-language-packs-optional"></a>Paso 6 - Instalar paquetes de idioma (opcional)

De manera predeterminada, el programa instalador intenta hacer coincidir el idioma del sistema operativo cuando se ejecuta por primera vez. Para instalar Visual Studio en un idioma de su elección, elija la pestaña **Paquetes de idioma** del Instalador de Visual Studio y siga las indicaciones.

::: moniker range="vs-2017"

  ![Visual Studio 2017 - Instalar paquetes de idioma](media/vs-installer-installing-language-packs.png "Instalar paquetes de idioma de Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

  ![Visual Studio 2019: Instalación de paquetes de idioma](media/vs-2019/vs-installer-language-packs.png "Instalación de paquetes de idioma de Visual Studio")

::: moniker-end

### <a name="change-the-installer-language-from-the-command-line"></a>Cambio del idioma del instalador en la línea de comandos

Otra manera de cambiar el idioma predeterminado es mediante la ejecución del instalador desde la línea de comandos. Por ejemplo, puede forzar al instalador a utilizar el inglés utilizando el comando siguiente: `vs_installer.exe --locale en-US`. El instalador recordará esta configuración cuando se ejecute la próxima vez. El instalador admite los siguientes tokens de idioma: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru y tr-tr.

## <a name="step-7---select-the-installation-location-optional"></a>Paso 7: Seleccionar la ubicación de instalación (opcional)

::: moniker range="vs-2017"

**Novedad de la versión 15.7**: ahora puede reducir la superficie de instalación de Visual Studio en la unidad del sistema. Puede mover la caché de descarga, los componentes compartidos, SDK y herramientas a distintas unidades y mantener Visual Studio en la unidad que lo ejecuta más rápido.

  ![Visual Studio 2017: Cambio de la ubicación de instalación](media/installation-options-by-location.png "Cambio de la ubicación de instalación")

::: moniker-end

::: moniker range="vs-2019"

Puede reducir la superficie de memoria de instalación de Visual Studio en la unidad del sistema. Puede mover la caché de descarga, los componentes compartidos, SDK y herramientas a distintas unidades y mantener Visual Studio en la unidad que lo ejecuta más rápido.

  ![Selección de ubicaciones de instalación de Visual Studio 2019](media/vs-2019/vs-installer-installation-locations.png "Seleccione la ubicación de instalación")

::: moniker-end

> [!IMPORTANT]
> Solo puede seleccionar una unidad diferente al instalar Visual Studio por primera vez. Si ya lo ha instalado y quiere cambiar de unidad, debe desinstalar Visual Studio y volver a instalarlo.

Para obtener más información, vea la página [Selección de las ubicaciones de instalación en Visual Studio](change-installation-locations.md).

## <a name="step-8---start-developing"></a>Paso 8: Empezar a desarrollar

::: moniker range="vs-2017"

1. Cuando la instalación de Visual Studio haya finalizado, elija el botón **Iniciar** para empezar a desarrollar con Visual Studio.

2. Elija **Archivo** y, luego, **Nuevo proyecto**.

3. Seleccione un tipo de proyecto.

   Por ejemplo, para [compilar una aplicación de C++](/cpp/get-started/tutorial-console-cpp), elija **Instalados**, expanda **Visual C++** y seleccione el tipo de proyecto de C++ que quiera compilar.

   Para [compilar una aplicación de C#](../get-started/csharp/tutorial-console.md), elija **Instalados**, expanda **Visual C#** y seleccione el tipo de proyecto de C# que quiera compilar.

::: moniker-end

::: moniker range="vs-2019"

1. Cuando la instalación de Visual Studio haya finalizado, elija el botón **Iniciar** para empezar a desarrollar con Visual Studio.

1. En la ventana de inicio, elija **Crear un proyecto nuevo**.

1. En el cuadro de búsqueda, escriba el tipo de aplicación que quiera crear para ver una lista de plantillas disponibles. La lista de plantillas depende de las cargas de trabajo que eligió durante la instalación. Para ver diferentes plantillas, elija diferentes cargas de trabajo.

   También puede filtrar la búsqueda de un lenguaje de programación específico mediante la lista desplegable **Lenguaje**. Además, puede filtrar mediante la lista **Plataforma** y la lista **Tipo de proyecto**.

1. Visual Studio abre el nuevo proyecto y ya se puede empezar programar.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Actualizar Visual Studio](update-visual-studio.md)
* [Modificar Visual Studio](modify-visual-studio.md)
* [Desinstalar Visual Studio](uninstall-visual-studio.md)
* [Crear una instalación sin conexión de Visual Studio](create-an-offline-installation-of-visual-studio.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Instalación de Visual Studio para Mac](/visualstudio/mac/installation)
