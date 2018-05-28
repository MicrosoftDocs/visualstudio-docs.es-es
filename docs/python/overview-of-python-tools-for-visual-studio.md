---
title: Introducción a la compatibilidad de Python en Visual Studio en Windows
description: Resumen de características de Python en Visual Studio, que lo convierten en el mejor IDE de Python en Windows (también conocidas como Herramientas de Python para Visual Studio, PTVS).
ms.date: 05/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 587517bdeabf9755e2678b03206059ef5b403255
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
---
# <a name="working-with-python-in-visual-studio-on-windows"></a>Trabajo con Python en Visual Studio en Windows

Python es un lenguaje de programación popular confiable, flexible, fácil de aprender, de uso libre en todos los sistemas operativos y admitido por una gran comunidad de desarrolladores y muchas bibliotecas gratuitas. Python es compatible con todos los modos de desarrollo, lo que incluye aplicaciones web, servicios web, aplicaciones de escritorio, scripting e informática científica, y lo utilizan muchas universidades, científicos, programadores ocasionales y desarrolladores profesionales. Puede obtener más información sobre el lenguaje en [python.org](https://www.python.org) y [Python for Beginners](https://www.python.org/about/gettingstarted/) (Python para principiantes).

Visual Studio es un potente IDE de Python en Windows. Visual Studio proporciona compatibilidad con [código abierto](https://github.com/Microsoft/ptvs) para el lenguaje Python a través del desarrollo de Python y las cargas de trabajo de ciencia de datos (Visual Studio 2017) y la extensión gratuita Herramientas de Python para Visual Studio (Visual Studio 2015 y versiones anteriores).

Python no se admite actualmente en Visual Studio para Mac, pero está disponible en Mac y Linux a través de Visual Studio Code (vea las [preguntas y respuestas](#questions-and-answers)).

Para comenzar:

- Siga las [instrucciones de instalación](installing-python-support-in-visual-studio.md) para configurar la carga de trabajo de Python.
- Familiarícese con las capacidades de Python de Visual Studio a través de las secciones de este artículo. También puede [ver una serie de vídeos (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121) en que se ofrece una introducción a Python en Visual Studio (22 minutos en total).
- Consulte una o varias de las guías de inicio rápido para crear un proyecto. Si no está seguro, comience por [Create a web app with Flask (Crear una aplicación web con Flask)](../ide/quickstart-python.md?context=visualstudio/python/default).
- Siga el tutorial [Working with Python in Visual Studio (Trabajar con Python en Visual Studio)](tutorial-working-with-python-in-visual-studio-step-01-create-project.md) para obtener una guía completa.

## <a name="support-for-multiple-interpreters"></a>Compatibilidad con diversos intérpretes

La ventana **Entornos de Python** de Visual Studio (se muestra a continuación en una vista amplia y expandida) proporciona un lugar único para administrar todos los entornos de Python globales, los entornos de conda y los entornos virtuales. Visual Studio detecta automáticamente las instalaciones de Python en ubicaciones estándares y le permite configurar las instalaciones personalizadas. Con cada entorno, puede administrar fácilmente paquetes, abrir una ventana interactiva para ese entorno y tener acceso a carpetas de entorno.

![Vista expandida de la ventana Entornos de Python](media/environments-expanded-view.png)

Para obtener más información:

- Vídeo (2' 35''): [Administración de Entornos de Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567)
- Documento: [Administración de Entornos de Python](managing-python-environments-in-visual-studio.md)
- Documento: [Referencia de la ventana Entornos de Python](python-environments-window-tab-reference.md)

## <a name="rich-editing-intellisense-and-code-comprehension"></a>Edición enriquecida, IntelliSense y comprensión del código

Visual Studio proporciona un editor de Python de primera clase, que incluye colores de la sintaxis, autocompletar en el código y las bibliotecas, formato de código, ayuda para las firmas, refactorización, detección de errores (se muestra a continuación) y sugerencias de tipo. Visual Studio también proporciona características exclusivas como vista de clases, ir a definición, buscar todas las referencias y fragmentos de código. La integración directa con la [Ventana interactiva](#interactive-window) lo ayudará a desarrollar rápidamente código Python que ya está guardado en un archivo.

![Finalizaciones de código para código de Python en Visual Studio](media/code-editing-completions-simple.png)

Para obtener más información:

- Vídeo (2' 30''): [Edición de código Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=r2iQH5LWE_4605918567)
- Documento: [Edición de código de Python](editing-python-code-in-visual-studio.md)
- Documento: [Formato del código](formatting-python-code.md)
- Documento: [Refactorización](refactoring-python-code.md)
- Documento: [Detección de errores](linting-python-code.md)
- Documentos de características generales de Visual Studio: [Características del editor de código](../ide/writing-code-in-the-code-and-text-editor.md).

## <a name="interactive-window"></a>Ventana interactiva

Para cada entorno de Python que Visual Studio conozca, puede abrir fácilmente el mismo entorno (REPL) interactivo para un intérprete Python directamente dentro de Visual Studio, en lugar de usar un símbolo del sistema independiente. También puede cambiar fácilmente entre entornos.

![Ventana interactiva de Python en Visual Studio](media/interactive-window.png)

Visual Studio también proporciona una estrecha integración entre el editor de código de Python y la ventana interactiva. Mediante el método abreviado de teclado **Ctrl+Entrar**, la línea (o el bloque) de código actual presente en el editor se envía cómodamente a la ventana interactiva y, a continuación, se pasa a la línea (o bloque) siguiente. El método abreviado **Ctrl + Entrar** le permite revisar fácilmente el código sin tener que ejecutar el depurador. Puede también enviar código seleccionado a la ventana interactiva con la misma pulsación de tecla y pegar fácilmente el código desde la ventana interactiva en el editor. Juntas, estas capacidades le permiten determinar los detalles de un segmento de código en la ventana interactiva y guardar fácilmente los resultados en un archivo en el editor.

Visual Studio también es compatible con IPython o Jupytr en REPL, incluidos gráficos en línea, .NET y Windows Presentation Foundation (WPF).

Para obtener más información:

- Vídeo (2' 22''): [Ventana interactiva de Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=gJYKY5LWE_4605918567)
- Documento: [Ventana interactiva](python-interactive-repl-in-visual-studio.md)
- Documento: [IPython en Visual Studio](interactive-repl-ipython.md)

## <a name="project-system-and-project-and-item-templates"></a>Sistema de proyecto y plantillas de proyecto y de elemento

Visual Studio lo ayuda a administrar la complejidad de un proyecto a medida que se desarrolla con el tiempo. Un proyecto es mucho más que una estructura de carpetas: incluye una descripción de cómo se utilizan distintos archivos y cómo se relacionan entre sí. Visual Studio lo ayuda a distinguir el código de aplicación, el código de prueba, las páginas web, JavaScript, los scripts de compilación, etcétera, lo cual, posteriormente, habilita las características apropiadas para los archivos. Además, una solución de Visual Studio lo ayuda a administrar varios proyectos relacionados, como por ejemplo, un proyecto de Python y un proyecto de extensión de C++.

![Una solución de Visual Studio que contiene proyectos de Python y C++](media/projects-solution-explorer-two-projects.png)

Las plantillas de proyecto y elemento automatizan el proceso de configuración de distintos tipos de proyectos y archivos, le permiten ahorrar tiempo y evitan que tenga que administrar detalles complejos y propensos a errores. Visual Studio proporciona plantillas para web, Azure, ciencia de datos, consola y otros tipos de proyectos, junto con las plantillas para archivos, como clases de Python, pruebas unitarias, configuración web de Azure, HTML e incluso aplicaciones Django.

[![Plantillas de elementos y proyectos de Python en Visual Studio](media/project-and-item-templates.png)](media/project-and-item-templates.png)

Para obtener más información:

- Documento: [Administración de proyectos de Python](managing-python-projects-in-visual-studio.md)
- Documento: [Referencia de plantillas de elemento](python-item-templates.md)
- Documento: [Plantillas de proyecto de Python](managing-python-projects-in-visual-studio.md#project-templates)
- Documento: [Trabajo con C++ y Python](working-with-c-cpp-python-in-visual-studio.md)
- Documento de características generales de Visual Studio: [Plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md#visual-studio-templates)
- Documento de características generales de Visual Studio: [Soluciones y proyectos en Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)

## <a name="full-featured-debugging"></a>Depuración repleta de características

Uno de los puntos fuertes de Visual Studio es su depurador potente. Para Python en particular, Visual Studio incluye depuración en modo mixto Python/C++, depuración remota en Linux, depuración remota en Azure, depuración en la ventana interactiva y depuración de las pruebas unitarias de Python.

![Depurador de Visual Studio para Python que muestra un menú emergente de excepción](media/debugging-exception-popup.png)

Para obtener más información:

- Vídeo: [Depuración de Python 3' 32''](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=Ep5dp5LWE_3805918567)
- Documento: [Depuración de Python](debugging-python-in-visual-studio.md)
- Documento: [Depuración en modo mixto Python/C++](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- Documento: [Depuración remota en Linux](debugging-python-code-on-remote-linux-machines.md)
- Documento: [Depuración remota en Azure](debugging-remote-python-code-on-azure.md)
- Documento de características generales de Visual Studio: [Resumen de características del depurador de Visual Studio](../debugger/debugger-feature-tour.md)

## <a name="profiling-tools-with-comprehensive-reporting"></a>Herramientas de generación de perfiles con informes completos

La generación de perfiles examina cómo se invierte el tiempo en la aplicación. Visual Studio admite la generación de perfiles con intérpretes basados en CPython e incluye la capacidad de comparar el rendimiento entre diferentes ejecuciones de generación de perfiles.

[![Resultados del generador de perfiles de Visual Studio para un proyecto de Python](media/profiling-results.png)](media/profiling-results.png)

Para obtener más información:

- Vídeo: [Generación de perfiles de Python 3' 00''](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=s6FoC6LWE_1005918567)
- Documento: [Herramientas de generación de perfiles de Python](profiling-python-code-in-visual-studio.md)
- Documentos de características generales de Visual Studio: [Resumen de las características de generación de perfiles](../profiling/profiling-feature-tour.md). (No todas las características de generación de perfiles de Visual Studio están disponibles para Python).

## <a name="unit-testing-tools"></a>Herramientas de pruebas unitarias

Detecte, ejecute y administre pruebas en el Explorador de pruebas de Visual Studio y depure fácilmente pruebas unitarias.

![Depuración de una prueba unitaria de Python en Visual Studio](media/unit-test-debugging.png)

Para obtener más información:

- Vídeo: [Pruebas de Python 2' 31''](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=hb46k6LWE_405918567)
- Documento: [Herramientas de pruebas unitarias de Python](unit-testing-python-in-visual-studio.md)
- Documentos de características generales de Visual Studio: [Prueba unitaria de su código](../test/unit-test-your-code.md).

## <a name="publishing-to-azure-and-azure-sdk-for-python"></a>Publicar en Azure y SDK de Azure para Python

Visual Studio proporciona compatibilidad integrada para publicar aplicaciones web y servicios en la nube en Azure. Visual Studio incluye plantillas de elemento de `web.config` esenciales para contenido dinámico y estático. La carga de trabajo de Python también incluye el SDK de Azure para Python, lo que simplifica el consumo de servicios de Azure desde aplicaciones de Windows, Mac OS X y Linux.

![Publicar una aplicación de Python en Azure en Visual Studio](media/azure-publish-dialog.png)

Para obtener más información:

- Documento: [Publicación en Azure](publishing-python-web-applications-to-azure-from-visual-studio.md)
- Documento: [SDK de Azure para Python](azure-sdk-for-python.md)

## <a name="python-training-on-microsoft-virtual-academy"></a>Aprendizaje de Python en Microsoft Virtual Academy

|   |   |
|---|---|
| ![icono de cámara de película para vídeo](../install/media/video-icon.png "Ver un vídeo") | <ul><li>[Introduction to Programming with Python](https://mva.microsoft.com/en-US/training-courses/introduction-to-programming-with-python-8360?l=lqhuMxFz_8904984382) (Introducción a la programación con Python)</li><li>[Python Beginner: Strings and Functions](https://mva.microsoft.com/en-US/training-courses/python-beginner-strings-and-functions-18015) (Python para principiantes: funciones y cadenas)</li><li>[Python Fundamentals: List and Loops](https://mva.microsoft.com/en-US/training-courses/python-fundamentals-lists-and-loops-18019) (Conceptos básicos de Python: listas y bucles)</li><li>[Top Python Questions](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121) (Principales preguntas sobre Python)</li></ul> |

## <a name="questions-and-answers"></a>Preguntas y respuestas

**P. ¿Visual Studio para Mac es compatible con Python?**

R. No en este momento, pero puede votar a favor de la solicitud en [UserVoice](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac/suggestions/18670291-python-tools-for-visual-studio-mac). La documentación de [Visual Studio para Mac](/visualstudio/mac/) identifica los tipos actuales de desarrollo que admite. Mientras tanto, Visual Studio Code en Windows, Mac y Linux [funciona bien con Python a través de las extensiones disponibles](https://code.visualstudio.com/docs/languages/python).

**P. ¿Qué puedo usar para generar la interfaz de usuario con Python?**

R. La oferta principal en este área es [Qt Project](https://www.qt.io/qt-for-application-development/), con enlaces para Python denominados [PySide (el enlace oficial)](http://wiki.qt.io/PySide) (vea también las [descargas de PySide](https://download.qt.io/official_releases/pyside/.)) y [PyQt](https://wiki.python.org/moin/PyQt). En la actualidad, la compatibilidad con Python en Visual Studio no incluye herramientas específicas para el desarrollo de la interfaz de usuario.

**P. ¿Un proyecto de Python puede producir un archivo ejecutable independiente?**

R. Por lo general, Python es un lenguaje interpretado, con código que se ejecuta bajo demanda en un entorno compatible con Python adecuado como Visual Studio y servidores web. En la actualidad, Visual Studio no proporciona por sí mismo los medios para crear un archivo ejecutable independiente, lo que significa básicamente un programa con un intérprete de Python insertado. En cambio, existen varios medios dentro de la comunidad de Python para crear ejecutables como se describe en [StackOverflow](http://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython también se puede insertar en una aplicación nativa, como se describe en la entrada de blog [Using CPython's Embeddable Zip File](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/26/cpython-embeddable-zip-file/) (Uso del archivo Zip insertable de CPython).

## <a name="features-matrix"></a>Matriz de características

Las características de Python se pueden instalar en las siguientes ediciones de Visual Studio, tal y como se describe en la [guía de instalación](installing-python-support-in-visual-studio.md):

- [Visual Studio 2017 (todas las ediciones)](https://www.visualstudio.com/vs/)
- Visual Studio 2015 (todas las ediciones)
- Visual Studio 2013 Community Edition
- Visual Studio 2013 Express para Web, Update 2 o una versión posterior
- Visual Studio 2013 Express para escritorio, Update 2 o una versión posterior
- Visual Studio 2013 (edición Pro o una versión posterior)
- Visual Studio 2012 (edición Pro o una versión posterior)
- Visual Studio 2010 SP1 (edición Pro o una versión posterior; se necesita .NET 4.5)

Visual Studio 2015 y las versiones anteriores están disponibles en [visualstudio.com/vs/older-downloads/](https://www.visualstudio.com/vs/older-downloads/).

> [!Important]
> Las características son totalmente compatibles y se mantienen para la versión más reciente de Visual Studio exclusivamente. Estas características están disponibles en versiones anteriores, pero no se mantienen de manera activa.

| Compatibilidad de Python | 2017 | 2015 | 2013 Comm | 2013 Escritorio | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Administrar varios intérpretes | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Detección automática de intérpretes populares | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Agregar intérpretes personalizados | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Entornos virtuales | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Pip e instalación sencilla | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Sistema de proyectos | 2017 | 2015 | 2013 Comm | 2013 Escritorio | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Nuevo proyecto a partir de código existente | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Mostrar todos los archivos | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Control de código fuente | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Integración con Git | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004;<sup>1</sup> | &#10007; |
<br/>

| Editar | 2017 | 2015 | 2013 Comm | 2013 Escritorio | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Resalte de sintaxis | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Autocompletar | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Ayuda para la firma | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Información rápida | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Examinador de objetos o vista de clases | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Barra de navegación | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Ir a definición | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Navegar a | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Buscar todas las referencias | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Sangría automática | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Formateo del código | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Refactorizar - Cambiar nombre | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Refactorizar - Extraer método | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Refactorizar - Agregar y quitar informe | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| PyLint | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Ventana interactiva | 2017 | 2015 | 2013 Comm | 2013 Escritorio | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Ventana interactiva | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| IPython con gráficos insertados | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Escritorio | 2017 | 2015 | 2013 Comm | 2013 Escritorio | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Aplicación de consola y Windows | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| WPF en IronPython (con diseñador XAML) | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Windows Forms en IronPython | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Web | 2017 | 2015 | 2013 Comm | 2013 Escritorio | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Proyecto web de Django | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Proyecto web de Bottle | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Proyecto web de Flask | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Proyecto web genérico | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Azure | 2017 | 2015 | 2013 Comm | 2013 Escritorio | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Implementación en el sitio web | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004;<sup>2</sup> |
| Implementación en el rol web | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| Implementación en el rol de trabajo | ? | ? | ? | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| Ejecución en el emulador de Azure | ? | ? | ? | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| Depuración remota | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> | &#10007; |
| Adjuntar en el Explorador de servidores | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> | &#10007; | &#10007; |
<br/>

| Plantillas de Django | 2017 | 2015 | 2013 Comm | 2013 Escritorio | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Depuración | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Autocompletar | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004; | &#10004; |
| Autocompletar para CSS y JavaScript | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007; | &#10007; |
<br/>

| Depuración | 2017 | 2015 | 2013 Comm | 2013 Escritorio | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Depuración | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Depuración sin un proyecto | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Depuración - Adjuntar a la edición | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; |
| Depuración en modo mixto | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| Depuración remota (Windows, Mac OS X y Linux) | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; |
| Ventana interactiva de depuración | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

<a name="matrix-profiling"></a>

| Generación de perfiles | 2017 | 2015 | 2013 Comm | 2013 Escritorio | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Generación de perfiles | &#10004; | &#10004; | &#10004; | &#10007; | &#10007; | &#10004; | &#10004; | &#10004; |
<br/>

| Prueba | 2017 | 2015 | 2013 Comm | 2013 Escritorio | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Explorador de pruebas | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| Ejecutar prueba | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| Depurar prueba | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
<br/>

1. La compatibilidad de Git para Visual Studio 2012 está disponible en la extensión Visual Studio Tools para Git, disponible en la [Galería de Visual Studio](http://visualstudiogallery.msdn.microsoft.com/abafc7d6-dcaa-40f4-8a5e-d6724bdb980c).

1. La implementación del sitio Web de Azure requiere [Azure SDK para .NET 2.1 - Visual Studio 2010 SP1](http://go.microsoft.com/fwlink/?LinkId=313855). Las versiones más recientes no son compatibles con Visual Studio 2010.

1. La compatibilidad con el rol web y de trabajo de Azure requiere el [SDK de Azure SDK para .NET 2.3 - VS 2012](http://go.microsoft.com/fwlink/?LinkId=323511) o una versión posterior.

1. La compatibilidad con el rol web y de trabajo de Azure requiere el [SDK de Azure SDK para .NET 2.3 - VS 2013](http://go.microsoft.com/fwlink/?LinkId=323510) o una versión posterior.

1. El editor de plantillas de Django en Visual Studio 2013 tiene algunos problemas conocidos que se resuelven mediante la instalación de Update 2.

1. Requiere Windows 8 o una versión posterior. Visual Studio 2013 Express para Web no tiene el cuadro de diálogo Asociar al proceso, pero la depuración remota de sitios web de Azure sigue siendo posible mediante el comando Adjuntar depurador (Python) en el Explorador de servidores. La depuración remota requiere el [SDK de Azure para .NET 2.3 - Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkId=323510) o una versión posterior.

1. Requiere Windows 8 o una versión posterior. El comando Adjuntar depurador (Python) del Explorador de servidores requiere el [SDK de Azure para .NET 2.3 - Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkId=323510) o una versión posterior.

1. Requiere Windows 8 o una versión posterior.

## <a name="additional-resources"></a>Recursos adicionales

- [Puente de WFastCGI entre IIS y Python](https://pypi.org/p/wfastcgi) (pypi.org)
- [Cursos gratuitos de Python en Microsoft Virtual Academy](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)
- [Preguntas principales de Python en Microsoft Virtual Academy](https://aka.ms/mva-top-python-questions)
