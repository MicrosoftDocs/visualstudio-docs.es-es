---
title: Compatibilidad con Python en Visual Studio en Windows
titleSuffix: ''
description: Resumen de características de Python en Visual Studio, que lo convierten en el mejor IDE de Python en Windows (también conocidas como Herramientas de Python para Visual Studio, PTVS).
ms.date: 06/05/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5f86c3b146bb74a38910b151a80c3c2d439ef023
ms.sourcegitcommit: ab18c9d850192fc9ccec10961f1126e8b0cba8da
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2019
ms.locfileid: "73061165"
---
# <a name="work-with-python-in-visual-studio-on-windows"></a>Trabajar con Python en Visual Studio en Windows

Python es un lenguaje de programación popular confiable, flexible, fácil de aprender, de uso libre en todos los sistemas operativos y admitido por una gran comunidad de desarrolladores y muchas bibliotecas gratuitas. Python es compatible con todos los modos de desarrollo, lo que incluye aplicaciones web, servicios web, aplicaciones de escritorio, scripting e informática científica, y lo utilizan muchas universidades, científicos, programadores ocasionales y desarrolladores profesionales. Puede obtener más información sobre el lenguaje en [python.org](https://www.python.org) y [Python for Beginners](https://www.python.org/about/gettingstarted/) (Python para principiantes).

Visual Studio es un potente IDE de Python en Windows. Visual Studio proporciona compatibilidad con [código abierto](https://github.com/Microsoft/ptvs) para el lenguaje Python a través del **desarrollo de Python** y las cargas de trabajo de **ciencia de datos** (Visual Studio 2017 y versiones posteriores) y la extensión gratuita Herramientas de Python para Visual Studio (Visual Studio 2015 y versiones anteriores).

Python no se admite actualmente en Visual Studio para Mac, pero está disponible en Mac y Linux a través de Visual Studio Code (vea las [preguntas y respuestas](#questions-and-answers)).

Para comenzar:

- Siga las [instrucciones de instalación](installing-python-support-in-visual-studio.md) para configurar la carga de trabajo de Python.
- Familiarícese con las capacidades de Python de Visual Studio a través de las secciones de este artículo.
::: moniker range="vs-2017"
- Consulte una o varias de las guías de inicio rápido para crear un proyecto. Si no está seguro, comience por [Create a web app with Flask (Crear una aplicación web con Flask)](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json).
::: moniker-end
::: moniker range=">=vs-2019"
- Consulte una o varias de las guías de inicio rápido para crear un proyecto. Si no está seguro, empiece con [Inicio rápido: Apertura y ejecución de código de Python en una carpeta](quickstart-05-python-visual-studio-open-folder.md) o [Creación de una aplicación web con Flask](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json).
::: moniker-end
- Siga el tutorial [Trabajar con Python en Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md) para obtener una experiencia completa.

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio admite la versión 2.7 de Python, así como las versiones 3.5 a 3.7. Aunque es posible usar Visual Studio para editar el código escrito en otras versiones de Python, no se admiten oficialmente esas versiones y características como IntelliSense y la depuración podrían no funcionar. La compatibilidad con la versión 3.8 de Python aún está en desarrollo; consulte los detalles específicos sobre este [problema de compatibilidad en GitHub](https://github.com/microsoft/PTVS/issues/5822).
::: moniker-end

## <a name="support-for-multiple-interpreters"></a>Compatibilidad con diversos intérpretes

La ventana **Entornos de Python** de Visual Studio (se muestra a continuación en una vista amplia y expandida) proporciona un lugar único para administrar todos los entornos de Python globales, los entornos de conda y los entornos virtuales. Visual Studio detecta automáticamente las instalaciones de Python en ubicaciones estándares y le permite configurar las instalaciones personalizadas. Con cada entorno, puede administrar fácilmente paquetes, abrir una ventana interactiva para ese entorno y tener acceso a carpetas de entorno.

::: moniker range="vs-2017"
![Vista expandida de la ventana Entornos de Python](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Vista expandida de la ventana Entornos de Python](media/environments/environments-expanded-view-2019.png)
::: moniker-end

Use el comando **Abrir ventana interactiva** para ejecutar Python de forma interactiva en el contexto de Visual Studio. Use el comando **Abrir en PowerShell** para abrir una ventana de comandos independiente en la carpeta del entorno seleccionado. Desde esa ventana de comandos puede ejecutar cualquier script de Python.

Para obtener más información:

- [Administración de entornos de Python](managing-python-environments-in-visual-studio.md)
- [Referencia de entornos de Python](python-environments-window-tab-reference.md)

## <a name="rich-editing-intellisense-and-code-comprehension"></a>Edición enriquecida, IntelliSense y comprensión del código

Visual Studio proporciona un editor de Python de primera clase, que incluye colores de la sintaxis, autocompletar en el código y las bibliotecas, formato de código, ayuda para las firmas, refactorización, detección de errores y sugerencias de tipos. Visual Studio también proporciona características exclusivas como vista de clases, **ir a definición**, **buscar todas las referencias** y fragmentos de código. La integración directa con la [ventana interactiva](#interactive-window) lo ayudará a desarrollar rápidamente código Python que ya está guardado en un archivo.

![Finalizaciones de código para código de Python en Visual Studio](media/code-editing-completions-simple.png)

Para obtener más información:

- Documentación: [Edición de código de Python](editing-python-code-in-visual-studio.md)
- Documentación: [Código de formato](formatting-python-code.md)
- Documentación: [Refactorización de código](refactoring-python-code.md)
- Documentación: [Utilizar un linter](linting-python-code.md)
- Documentos de características generales de Visual Studio: [Características del editor de código](../ide/writing-code-in-the-code-and-text-editor.md)

## <a name="interactive-window"></a>Ventana interactiva

Para cada entorno de Python que Visual Studio conozca, puede abrir fácilmente el mismo entorno (REPL) interactivo para un intérprete Python directamente dentro de Visual Studio, en lugar de usar un símbolo del sistema independiente. También puede cambiar fácilmente entre entornos. (Para abrir un símbolo del sistema independiente, seleccione el entorno que quiera en la ventana **Entornos de Python** y seleccione el comando **Abrir en PowerShell** como se ha explicado anteriormente en [Compatibilidad con diversos intérpretes](#support-for-multiple-interpreters)).

![Ventana interactiva de Python en Visual Studio](media/interactive-window.png)

Visual Studio también proporciona una estrecha integración entre el editor de código de Python y la ventana **interactiva**. Mediante el método abreviado de teclado**Ctrl**+**Entrar**, la línea (o el bloque) de código actual presente en el editor se envía cómodamente a la ventana **interactiva** y, a continuación, se pasa a la línea (o bloque) siguiente. El método abreviado **Ctrl**+**Entrar** le permite revisar fácilmente el código sin tener que ejecutar el depurador. Puede también enviar código seleccionado a la ventana **interactiva** con la misma pulsación de tecla y pegar fácilmente el código desde la ventana **interactiva** en el editor. Juntas, estas capacidades le permiten determinar los detalles de un segmento de código en la ventana **interactiva** y guardar fácilmente los resultados en un archivo en el editor.

Visual Studio también es compatible con IPython o Jupyter en REPL, incluidos gráficos en línea, .NET y Windows Presentation Foundation (WPF).

Para obtener más información:

- [Ventana interactiva](python-interactive-repl-in-visual-studio.md)
- [IPython en Visual Studio](interactive-repl-ipython.md)

## <a name="project-system-and-project-and-item-templates"></a>Sistema de proyecto y plantillas de proyecto y de elemento

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio 2019 permite abrir una carpeta que contiene código de Python y ejecutar ese código sin crear archivos de solución y proyecto de Visual Studio. Para obtener más información, vea [Inicio rápido: Apertura y ejecución de código de Python en una carpeta](quickstart-05-python-visual-studio-open-folder.md). Sin embargo, usar un archivo del proyecto trae ventajas, como se explica en esta sección.
::: moniker-end

Visual Studio lo ayuda a administrar la complejidad de un proyecto a medida que se desarrolla con el tiempo. Un *proyecto de Visual Studio* es mucho más que una estructura de carpetas: incluye una descripción de cómo se utilizan distintos archivos y cómo se relacionan entre sí. Visual Studio lo ayuda a distinguir el código de aplicación, el código de prueba, las páginas web, JavaScript, los scripts de compilación, etcétera, lo cual, posteriormente, habilita las características apropiadas para los archivos. Además, una solución de Visual Studio lo ayuda a administrar varios proyectos relacionados, como por ejemplo, un proyecto de Python y un proyecto de extensión de C++.

![Una solución de Visual Studio que contiene proyectos de Python y C++](media/projects-solution-explorer-two-projects.png)

Las plantillas de proyecto y elemento automatizan el proceso de configuración de distintos tipos de proyectos y archivos, le permiten ahorrar tiempo y evitan que tenga que administrar detalles complejos y propensos a errores. Visual Studio proporciona plantillas para web, Azure, ciencia de datos, consola y otros tipos de proyectos, junto con las plantillas para archivos, como clases de Python, pruebas unitarias, configuración web de Azure, HTML e incluso aplicaciones Django.

[![Plantillas de elementos y proyectos de Python en Visual Studio](media/project-and-item-templates.png)](media/project-and-item-templates.png#lightbox)

Para obtener más información:

- Documentación: [Administración de proyectos de Python](managing-python-projects-in-visual-studio.md)
- Documentación: [Referencia de plantillas de elemento](python-item-templates.md)
- Documentación: [Plantillas de proyecto de Python](managing-python-projects-in-visual-studio.md#project-templates)
- Documentación: [Trabajo con C++ y Python](working-with-c-cpp-python-in-visual-studio.md)
- Documentos de características generales de Visual Studio: [Plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md#visual-studio-templates)
- Documentos de características generales de Visual Studio: [Soluciones y proyectos en Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)

## <a name="full-featured-debugging"></a>Depuración repleta de características

Uno de los puntos fuertes de Visual Studio es su depurador potente. Para Python en particular, Visual Studio incluye depuración en modo mixto Python/C++, depuración remota en Linux, depuración en la ventana **interactiva** y depuración de las pruebas unitarias de Python.

![Depurador de Visual Studio para Python que muestra un menú emergente de excepción](media/debugging-exception-popup.png)

::: moniker range=">=vs-2019"
En Visual Studio 2019, puede ejecutar y depurar código sin tener un archivo del proyecto de Visual Studio. Consulte [Inicio rápido: Apertura y ejecución de código de Python en una carpeta](quickstart-05-python-visual-studio-open-folder.md) para ver un ejemplo.
::: moniker-end

Para obtener más información:

- Documentación: [Depuración de Python](debugging-python-in-visual-studio.md)
- Documentación: [Depuración en modo mixto Python/C++](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- Documentación: [Depuración remota en Linux](debugging-python-code-on-remote-linux-machines.md)
- Documentos de características generales de Visual Studio: [Guía de características del depurador de Visual Studio](../debugger/debugger-feature-tour.md)

## <a name="profiling-tools-with-comprehensive-reporting"></a>Herramientas de generación de perfiles con informes completos

La generación de perfiles examina cómo se invierte el tiempo en la aplicación. Visual Studio admite la generación de perfiles con intérpretes basados en CPython e incluye la capacidad de comparar el rendimiento entre diferentes ejecuciones de generación de perfiles.

[![Resultados del generador de perfiles de Visual Studio para un proyecto de Python](media/profiling-results.png)](media/profiling-results.png#lightbox)

Para obtener más información:

- Documentación: [Herramientas de generación de perfiles de Python](profiling-python-code-in-visual-studio.md)
- Documentos de características generales de Visual Studio: [Guía de características de generación de perfiles](../profiling/profiling-feature-tour.md). (No todas las características de generación de perfiles de Visual Studio están disponibles para Python).

## <a name="unit-testing-tools"></a>Herramientas de pruebas unitarias

Detecte, ejecute y administre pruebas en el **Explorador de pruebas** de Visual Studio y depure fácilmente pruebas unitarias.

![Depuración de una prueba unitaria de Python en Visual Studio](media/unit-test-debugging.png)

Para obtener más información:

- Documentación: [Herramientas de pruebas unitarias de Python](unit-testing-python-in-visual-studio.md)
- Documentos de características generales de Visual Studio: [Prueba unitaria del código](../test/unit-test-your-code.md).

## <a name="azure-sdk-for-python"></a>SDK de Azure para Python

Las bibliotecas de Azure para Python simplifican el uso de servicios de Azure desde aplicaciones Windows, Mac OS X y Linux. Puede usarlas para crear y administrar recursos de Azure, así como para conectarse a servicios de Azure. 

Para obtener más información, vea [SDK de Azure para Python](/azure/python/) y [Bibliotecas de Azure para Python](/azure/python/python-sdk-azure-overview).

## <a name="questions-and-answers"></a>Preguntas y respuestas

**P. ¿Visual Studio para Mac es compatible con Python?**

R. No en este momento, pero puede votar a favor de la solicitud en la [comunidad de desarrolladores](https://developercommunity.visualstudio.com/content/idea/351820/python-tools-for-visual-studio-mac.html). La documentación de [Visual Studio para Mac](/visualstudio/mac/) identifica los tipos actuales de desarrollo que admite. Mientras tanto, Visual Studio Code en Windows, Mac y Linux [funciona bien con Python a través de las extensiones disponibles](https://code.visualstudio.com/docs/languages/python).

**P. ¿Qué puedo usar para generar la interfaz de usuario con Python?**

R. La oferta principal en este área es [Qt Project](https://www.qt.io/qt-for-application-development/), con enlaces para Python denominados [PySide (el enlace oficial)](https://wiki.qt.io/PySide) (vea también las [descargas de PySide](https://download.qt.io/official_releases/pyside/.)) y [PyQt](https://wiki.python.org/moin/PyQt). En la actualidad, la compatibilidad con Python en Visual Studio no incluye herramientas específicas para el desarrollo de la interfaz de usuario.

**P. ¿Un proyecto de Python puede producir un archivo ejecutable independiente?**

R. Por lo general, Python es un lenguaje interpretado, con código que se ejecuta bajo demanda en un entorno compatible con Python adecuado como Visual Studio y servidores web. En la actualidad, Visual Studio no proporciona por sí mismo los medios para crear un archivo ejecutable independiente, lo que significa básicamente un programa con un intérprete de Python insertado. En cambio, la comunidad de Python ha proporcionado varios medios para crear ejecutables como se describe en [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython también se puede insertar en una aplicación nativa, como se describe en la entrada de blog [Using CPython's Embeddable Zip File](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/) (Uso del archivo Zip insertable de CPython).

::: moniker range="<=vs-2017"

## <a name="feature-support"></a>Compatibilidad con las características

Las características de Python se pueden instalar en las siguientes ediciones de Visual Studio, tal y como se describe en la [guía de instalación](installing-python-support-in-visual-studio.md):

- [Visual Studio 2019 (todas las ediciones)](https://visualstudio.microsoft.com/vs/)
- Visual Studio 2017 (todas las ediciones)
- Visual Studio 2015 (todas las ediciones)
- Visual Studio 2013 Community Edition
- Visual Studio 2013 Express para Web, Update 2 o una versión posterior
- Visual Studio 2013 Express para escritorio, Update 2 o una versión posterior
- Visual Studio 2013 (edición Pro o una versión posterior)
- Visual Studio 2012 (edición Pro o una versión posterior)
- Visual Studio 2010 SP1 (edición Pro o una versión posterior; se necesita .NET 4.5)

Visual Studio 2015 y las versiones anteriores están disponibles en [visualstudio.microsoft.com/vs/older-downloads/](https://visualstudio.microsoft.com/vs/older-downloads/).

> [!Important]
> Las características son totalmente compatibles y se mantienen para la versión más reciente de Visual Studio exclusivamente. Estas características están disponibles en versiones anteriores, pero no se mantienen de manera activa.

|          Compatibilidad de Python          |   2017+   |   2015   | 2013 Comm | 2013 Escritorio | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|----------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|   Administrar varios intérpretes   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Detección automática de intérpretes populares | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Agregar intérpretes personalizados      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Entornos virtuales       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Pip e instalación sencilla         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Sistema de proyectos         |   2017+   |   2015   | 2013 Comm | 2013 Escritorio | 2013 Web | 2013 Pro+ |      2012 Pro+       | 2010 SP1 Pro+ |
|--------------------------------|----------|----------|-----------|--------------|----------|-----------|----------------------|---------------|
| Nuevo proyecto a partir de código existente | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         Mostrar todos los archivos         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         Control de código fuente         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|        Integración con Git         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;<sup>1</sup> |   &#10007;    |

<br/>

|           Editar            |   2017+   |   2015   | 2013 Comm | 2013 Escritorio | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Resalte de sintaxis      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Autocompletar         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Ayuda para la firma        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|          Información rápida          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Examinador de objetos o vista de clases   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Barra de navegación        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Ir a definición       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Navegar a          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Buscar todas las referencias      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Sangría automática       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Formateo del código        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      Refactorizar - Cambiar nombre       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Refactorizar - Extraer método   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Refactorizar - Agregar y quitar informe | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|            PyLint            | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|     Ventana interactiva     |   2017+   |   2015   | 2013 Comm | 2013 Escritorio | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|----------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Ventana interactiva     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| IPython con gráficos insertados | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|               Escritorio               |   2017+   |   2015   | 2013 Comm | 2013 Escritorio | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|-------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Aplicación de consola y Windows     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| WPF en IronPython (con diseñador XAML) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      Windows Forms en IronPython       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Web         |   2017+   |   2015   | 2013 Comm | 2013 Escritorio | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Proyecto web de Django  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Proyecto web de Bottle  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Proyecto web de Flask  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Proyecto web genérico | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Azure          |   2017+   |   2015   | 2013 Comm | 2013 Escritorio |       2013 Web       |      2013 Pro+       |      2012 Pro+       |    2010 SP1 Pro+     |
|------------------------|----------|----------|-----------|--------------|----------------------|----------------------|----------------------|----------------------|
|   Implementación en el sitio web   | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       |       &#10004;       | &#10004;<sup>2</sup> |
|   Implementación en el rol web   | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Implementación en el rol de trabajo  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Ejecución en el emulador de Azure  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
|    Depuración remota    | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> |       &#10007;       |
| Adjuntar en el Explorador de servidores | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> |       &#10007;       |       &#10007;       |

<br/>

|           Plantillas de Django           |   2017+   |   2015   | 2013 Comm | 2013 Escritorio |       2013 Web       |      2013 Pro+       | 2012 Pro+ | 2010 SP1 Pro+ |
|--------------------------------------|----------|----------|-----------|--------------|----------------------|----------------------|-----------|---------------|
|              Depuración               | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       | &#10004;  |   &#10004;    |
|            Autocompletar             | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004;  |   &#10004;    |
| Autocompletar para CSS y JavaScript | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007;  |   &#10007;    |

<br/>

|                  Depuración                  |   2017+   |   2015   | 2013 Comm | 2013 Escritorio | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|                  Depuración                  | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Depuración sin un proyecto         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Depuración - Adjuntar a la edición        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|            Depuración en modo mixto             | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
| Depuración remota (Windows, Mac OS X y Linux) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|          Ventana interactiva de depuración           | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

<a name="matrix-profiling"></a>

| Generación de perfiles |   2017+   |   2015   | 2013 Comm | 2013 Escritorio | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|-----------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Generación de perfiles | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|     Prueba      |   2017+   |   2015   | 2013 Comm | 2013 Escritorio | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Explorador de pruebas | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|   Ejecutar prueba    | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|  Depurar prueba   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |

<br/>

1. La compatibilidad de Git para Visual Studio 2012 está disponible en la extensión Visual Studio Tools para Git, disponible en [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TFSPowerToolsTeam.VisualStudioToolsforGit).

1. La implementación del sitio Web de Azure requiere [Azure SDK para .NET 2.1 - Visual Studio 2010 SP1](https://go.microsoft.com/fwlink/?LinkId=313855). Las versiones más recientes no son compatibles con Visual Studio 2010.

1. La compatibilidad con el rol web y de trabajo de Azure requiere el [SDK de Azure SDK para .NET 2.3 - VS 2012](https://go.microsoft.com/fwlink/?LinkId=323511) o una versión posterior.

1. La compatibilidad con el rol web y de trabajo de Azure requiere el [SDK de Azure SDK para .NET 2.3 - VS 2013](https://go.microsoft.com/fwlink/?LinkId=323510) o una versión posterior.

1. El editor de plantillas de Django en Visual Studio 2013 tiene algunos problemas conocidos que se resuelven mediante la instalación de Update 2.

1. Requiere Windows 8 o una versión posterior. Visual Studio 2013 Express para Web no tiene el cuadro de diálogo **Asociar al proceso**, pero la depuración remota de sitios web de Azure sigue siendo posible mediante el comando **Adjuntar depurador (Python)** en el **Explorador de servidores**. La depuración remota requiere el [SDK de Azure para .NET 2.3 - Visual Studio 2013](https://go.microsoft.com/fwlink/?LinkId=323510) o una versión posterior.

1. Requiere Windows 8 o una versión posterior. El comando **Adjuntar depurador (Python)** del **Explorador de servidores** requiere el [SDK de Azure para .NET 2.3 - Visual Studio 2013](https://go.microsoft.com/fwlink/?LinkId=323510) o una versión posterior.

1. Requiere Windows 8 o una versión posterior.
::: moniker-end
