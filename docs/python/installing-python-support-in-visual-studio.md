---
title: Instalación de la compatibilidad de Python en Visual Studio | Microsoft Docs
description: Instrucciones detalladas sobre cómo instalar las Herramientas de Python para Visual Studio (PTVS) en Visual Studio 2017, 2015, 2013, 2012 y 2010, incluidas las opciones y las ubicaciones de instalación.
ms.custom: ''
ms.date: 02/15/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: ''
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: faa901c14bd5d115aa3e7384a5d3b63c0410b64b
ms.sourcegitcommit: 236c250bb97abdab99d00c6525d106fc0035d7d0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2018
---
# <a name="installing-python-support-in-visual-studio-on-windows"></a>Instalación de la compatibilidad con Python en Visual Studio en Windows

Para instalar la compatibilidad de Python para Visual Studio (también conocida como Herramientas de Python para Visual Studio o PTVS), siga las instrucciones que aparecen en la sección correspondiente a su versión de Visual Studio:

- [Visual Studio 2017](#visual-studio-2017)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 y anterior](#visual-studio-2013-and-earlier)

En Visual Studio 2015 y versiones anteriores, también tiene que [instalar un intérprete de Python](installing-python-interpreters.md) por separado que prefiera (Python 3.5 o versiones anteriores; la versión 3.6 no es compatible y generará el mensaje "Versión 3.6 de Python no compatible"). En la misma página también se incluyen instrucciones para agregar un intérprete de Python existente a Visual Studio 2017.

Para probar rápidamente la compatibilidad de Python después de seguir los pasos de instalación, abra la ventana interactiva de Python; para ello, presione Alt-I y escriba `2+2`. Si no ve la salida de `4`, revise los pasos.

> [!Tip]
> La carga de trabajo de Python incluye la útil extensión Cookiecutter que proporciona una interfaz gráfica de usuario para detectar plantillas, opciones de plantilla de entrada y crear proyectos y archivos. Para obtener más información, consulte [Uso de la extensión Cookiecutter](using-python-cookiecutter-templates.md).

> [!Note]
> La compatibilidad con Python no está actualmente disponible en Visual Studio para Mac, pero está disponible en Mac y Linux a través de Visual Studio Code. Consulte las [preguntas y respuestas](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

## <a name="visual-studio-2017"></a>Visual Studio 2017

1. Descargue y ejecute el instalador de Visual Studio 2017 más reciente. Si tiene Visual Studio ya instalado, ejecute el instalador de Visual Studio, seleccione las opciones **Modificar** (consulte [Modificar Visual Studio](../install/modify-visual-studio.md)) y vaya al paso 2.

    > [!div class="nextstepaction"]
    > <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Instalar Visual Studio 2017 Community</a>

    >[!Tip]
    > La edición Community es para desarrolladores individuales, aprendizaje en el aula, investigación académica y desarrollo de código abierto. Para otros usos, instale <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Visual Studio 2017 Professional</a> o <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Visual Studio 2017 Enterprise</a>.

1. El instalador muestra una lista de las cargas de trabajo, que son grupos de opciones relacionadas para áreas de desarrollo específicas. Para Python, seleccione la carga de trabajo **Desarrollo de Python**.

    ![Carga de trabajo de desarrollo de Python en el instalador de Visual Studio](media/installation-python-workload.png)

    Opcional: si está trabajando con la ciencia de datos, considere también la posibilidad de la carga de trabajo **Aplicaciones de ciencia de datos y de análisis**. Esta carga de trabajo incluye compatibilidad con Python y también con los lenguajes R y F#. Para más información, vea [Carga de trabajo Aplicaciones de ciencia de datos y de análisis](../rtvs/data-science-and-analytical-applications-workload.md).

    > [!Note]
    > Las cargas de trabajo de Python y Ciencia de datos solo están disponibles con Visual Studio 2017 versión 15.2 y posteriores.

1. En la parte derecha del instalador, puede elegir opciones adicionales si lo prefiere. Omita este paso para aceptar las opciones predeterminadas.

    ![Opciones de desarrollo de Python en el instalador de Visual Studio](media/installation-python-options.png)

    | Opción | Description |
    | --- | --- |
    | Distribuciones de Python | Elija cualquier combinación de las variantes de 32 bits y 64 bits de las distribuciones de Python 2, Python 3, Anaconda2 y Anaconda3 con las que piensa trabajar. En todas se incluye el intérprete, el runtime y las bibliotecas de la distribución. Anaconda, en concreto, es una plataforma abierta de ciencia de datos que incluye una gran variedad de paquetes preinstalados. (Puede volver al instalador de Visual Studio en cualquier momento para agregar o quitar distribuciones).  **Nota**: Si ha instalado una distribución fuera del instalador de Visual Studio, no es necesario comprobar la opción equivalente aquí. Visual Studio detecta automáticamente las instalaciones existentes de Python. Consulte [Entornos de Python](managing-python-environments-in-visual-studio.md). |
    | Compatibilidad con plantillas de Cookiecutter | Instala la interfaz de usuario gráfica de Cookiecutter para detectar plantillas, opciones de plantilla de entrada y crear proyectos y archivos. Vea [Uso de la extensión Cookiecutter](using-python-cookiecutter-templates.md). |
    | Compatibilidad web con Python | Instala herramientas para desarrollo web, incluida la compatibilidad de edición de HTML, CSS y JavaScript, junto con plantillas de proyectos que usan los marcos Bottle, Flask y Django. Vea [Plantillas de proyecto web de Python](python-web-application-project-templates.md). |
    | Compatibilidad con IoT de Python | Admite el desarrollo de Windows IoT Core con Python. |
    | Herramientas de desarrollo nativo de Python | Instala el compilador de C++ y otros componentes necesarios para desarrollar extensiones nativas para Python. Vea [Creación de una extensión de C++ para Python](working-with-c-cpp-python-in-visual-studio.md). Instale también la carga de trabajo **Desarrollo para el escritorio con C++** para disfrutar de una compatibilidad plena. |
    | Herramientas principales de Azure Cloud Services | Proporciona compatibilidad adicional para el desarrollador de Azure Cloud Services en Python. Vea [Proyectos de servicio de nube de Azure](python-azure-cloud-service-project-template.md). |

1. Después de la instalación, el instalador proporciona opciones para modificar, iniciar, reparar o desinstalar Visual Studio. El botón **Modificar** cambia a **Actualizar** cuando hay actualizaciones de Visual Studio disponibles para alguno de los componentes instalados. (Después, la opción Modificar está disponible en el menú desplegable). También puede iniciar Visual Studio y el instalador desde el menú Inicio de Windows mediante la búsqueda de "Visual Studio".

    ![Inicio, modificación o desinstalación de Visual Studio desde el instalador](media/installation-vs-launch.png)

|   |   |
|---|---|
| ![icono de cámara de película para vídeo](../install/media/video-icon.png "Ver un vídeo") | [Vea un vídeo (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Installing-Visual-Studio-Python-Support-go1id3LWE_1705918567) sobre cómo instalar la compatibilidad de Python en Visual Studio.|

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Ejecute el instalador de Visual Studio; para ello, vaya a **Panel de control > Programas y características**, seleccione **Microsoft Visual Studio 2015** y después haga clic en **Cambiar**.

1. En el instalador, seleccione **Modificar**.

1. Seleccione **Lenguajes de programación > Herramientas de Python para Visual Studio** y luego haga clic en **Siguiente**:

    ![Opción de PTVS en el instalador de Visual Studio 2015](media/installation-vs2015.png)

1. Una vez completada la instalación de Visual Studio, [instale un intérprete de Python de su elección](installing-python-interpreters.md). Si ya tiene instalado un intérprete y Visual Studio no lo detecta de manera automática, consulte [Identificación manual de un entorno existente](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment).

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 y anterior

1. Instale la versión adecuada de Herramientas de Python para Visual Studio para su versión de Visual Studio:

    - Visual Studio 2013: [PTVS 2.2 para Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2). En el cuadro de diálogo **Archivo > Nuevo proyecto** de Visual Studio 2013 se ofrece un acceso directo a este proceso.
    - Visual Studio 2012: [PTVS 2.1 para Visual Studio 2012](https://pytools.codeplex.com/downloads/get/920478)
    - Visual Studio 2010: [PTVS 2.1 para Visual Studio 2010](https://pytools.codeplex.com/downloads/get/920479)

1. [Instale un intérprete de Python de su elección](installing-python-interpreters.md). Si ya tiene instalado un intérprete y Visual Studio no lo detecta de manera automática, consulte [Identificación manual de un entorno existente](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment).

## <a name="install-locations"></a>Ubicaciones de instalación

De forma predeterminada, la compatibilidad de Python se instala para todos los usuarios de un equipo.

En Visual Studio 2017, la carga de trabajo de Python se instala en `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\<VS_edition>Common7\IDE\Extensions\Microsoft\Python`, donde &lt;VS_edition&gt; es Community, Professional o Enterprise.

En Visual Studio 2015 y versiones anteriores, las rutas de instalación son las siguientes:

- 32 bits:
  - Ruta de acceso: `%Program Files(x86)%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - Ubicación del Registro de ruta de acceso: `HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\<VS_ver>\InstallDir`
- 64 bits:
  - Ruta de acceso: `%Program Files%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - Ubicación del Registro de ruta de acceso: `HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\<VS_ver>\InstallDir`

donde:

- &lt;VS_ver&gt; es:
  - 14.0 para Visual Studio 2015
  - 12.0 para Visual Studio 2013
  - 11.0 para Visual Studio 2012
  - 10.0 para Visual Studio 2010
- &lt;PTVS_ver&gt; es un número de versión, como 2.2, 2.1, 2.0, 1.5, 1.1 o 1.0.

### <a name="user-specific-installations-15-and-earlier"></a>Instalaciones específicas de usuario (1.5 y anteriores)

Herramientas de Python para Visual Studio 1.5 y las versiones anteriores permitían una instalación solo para el usuario actual, en cuyo caso la ruta de instalación es `%LocalAppData%\Microsoft\VisualStudio\<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`, donde &lt;VS_ver&gt; y &lt;PTVS_ver&gt; se corresponden con las mismas versiones indicadas anteriormente.

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
