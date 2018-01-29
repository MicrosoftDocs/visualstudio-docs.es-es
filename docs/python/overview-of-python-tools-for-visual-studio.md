---
title: "Información general de la compatibilidad de Python en Visual Studio (Windows) | Microsoft Docs"
description: "Resumen de las características disponibles para Python en Visual Studio (también conocido como Herramientas de Python para Visual Studio, PTVS), incluidas las preguntas y respuestas( P+F) y la matriz de compatibilidad de características de las distintas versiones de Visual Studio."
ms.custom: 
ms.date: 01/09/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: hero-article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 067684c7b5064e096849afe69d2f0db1bcc75ea6
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2018
---
# <a name="working-with-python-in-visual-studio-windows"></a>Uso de Python en Visual Studio (Windows)

Python es un lenguaje de programación popular confiable, flexible, fácil de aprender, de uso libre en todos los sistemas operativos y admitido por una gran comunidad de desarrolladores y muchas bibliotecas gratuitas. Python es compatible con todos los modos de desarrollo, lo que incluye aplicaciones web, servicios web, aplicaciones de escritorio, scripting e informática científica, y lo utilizan muchas universidades, científicos, programadores ocasionales y desarrolladores profesionales. Puede obtener más información sobre el lenguaje en [python.org](https://www.python.org) y [Python for Beginners](https://www.python.org/about/gettingstarted/) (Python para principiantes).

Visual Studio en Windows proporciona compatibilidad con [código abierto](https://github.com/Microsoft/ptvs) para el lenguaje Python a través del desarrollo de Python y las cargas de trabajo de ciencia de datos (Visual Studio 2017) y la extensión gratuita Herramientas de Python para Visual Studio (Visual Studio 2015 y versiones anteriores). Python no se admite actualmente en Visual Studio para Mac, pero está disponible en Mac y Linux a través de Visual Studio Code (vea las [preguntas y respuestas](#questions-and-answers)).

Para comenzar:

- Siga las [instrucciones de instalación](installing-python-support-in-visual-studio.md) para configurar la carga de trabajo de Python.
- Consulte una o varias de las guías de inicio rápido para crear un proyecto. Si no está seguro, comience por [Create a project from a template (Crear un proyecto a partir de una plantilla)](quickstart-02-project-from-template.md).
- Siga el tutorial [Working with Python in Visual Studio (Trabajar con Python en Visual Studio)](tutorial-working-with-python-in-visual-studio-step-01-create-project.md) para obtener una guía completa.
- Luego, use los vínculos de la tabla siguiente para explorar las características relacionadas con Python y las funcionalidades de Visual Studio.

| Característica | Description | Documentación general de Visual Studio |
| --- | --- | --- |
| [Sistema de proyectos de Visual Studio](managing-python-projects-in-visual-studio.md) | Selecciona implícitamente una estructura de carpetas de código Python permitiendo al mismo tiempo el control explícito para identificar el código de la aplicación, el código de prueba, las páginas web, JavaScript, los scripts de compilación, etc. | [Soluciones y proyectos en Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Plantillas de proyecto](managing-python-projects-in-visual-studio.md#project-templates) | Crea rápidamente una estructura de proyecto para proyectos de consola, web, Azure, datos científicos, entre otros. | [Plantillas de Visual Studio](../ide/creating-project-and-item-templates.md#visual-studio-templates) |
| Compatibilidad con varios intérpretes | Admite varias versiones de CPython e IronPython. | N/D |
| Compatibilidad con IPython | Incluye compatibilidad para IPython o Jupyter en REPL para gráficos en línea, .NET y Windows Presentation Foundation (WPF). | N/D |
| [Edición enriquecida, IntelliSense y comprensión del código](code-editing.md) | Incluye colores de sintaxis, autocompletado en todo el código y las bibliotecas, [formateo de código](code-formatting.md), ayuda para las firmas, vista de clases, Ir a definición, Buscar todas las referencias, fragmentos de código, [refactorización](code-refactoring.md), [PyLint](code-pylint.md) y mucho más. | [Escribir código en el editor de código y texto](../ide/writing-code-in-the-code-and-text-editor.md) |
| [Ventana interactiva](interactive-repl.md) | Proporciona una experiencia rápida de REPL para Python con la capacidad de resaltar fácilmente una parte del código y enviarla a la ventana interactiva. | N/D |
| [Depuración repleta de características](debugging.md) | La depuración se puede realizar con o sin un proyecto de Visual Studio, lo que incluye la posibilidad de depurar un ejecutable existente, [Depuración en modo mixto de Python/C++](debugging-mixed-mode.md), [depuración remota](debugging-cross-platform-remote.md) en Windows/Linux/Mac, [depuración remota en Azure](debugging-azure-remote.md) y depuración en la ventana interactiva. | [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md) |
| [Herramientas de generación de perfiles con informes completos](profiling.md) | Explora cómo se invierte el tiempo dentro de la aplicación, incluida la capacidad de comparar el rendimiento entre diferentes ejecuciones de generación de perfiles. | [Herramientas de generación de perfiles](../profiling/profiling-tools.md) (no todas las características de generación de perfiles de Visual Studio están disponibles para Python) |
| [Herramientas de pruebas unitarias](unit-testing.md) | Detecte, ejecute y administre pruebas en el Explorador de pruebas de Visual Studio y depure fácilmente pruebas unitarias. | [Haga una prueba unitaria de su código](../test/unit-test-your-code.md) |

La carga de trabajo de Python también incluye el [SDK de Azure para Python](azure-sdk-for-python.md), lo que simplifica el consumo de servicios de Azure desde aplicaciones de Windows, Mac OS X y Linux.

Para ver un vídeo de introducción, consulte el breve curso [Python Tools for Visual Studio (Herramientas de Python para Visual Studio)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121) en Microsoft Virtual Academy (aproximadamente 22 minutos en total). 

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Installing-Visual-Studio-Python-Support-go1id3LWE_1705918567]

## <a name="questions-and-answers"></a>Preguntas y respuestas

**P. ¿Visual Studio para Mac es compatible con Python?**

R. No en este momento, aunque se ha solicitado en [UserVoice](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac/suggestions/18670291-python-tools-for-visual-studio-mac). La documentación de [Visual Studio para Mac](/visualstudio/mac/) identifica los tipos actuales de desarrollo que admite. Mientras tanto, Visual Studio Code en Windows, Mac y Linux [funciona bien con Python a través de las extensiones disponibles](https://code.visualstudio.com/docs/languages/python).

**P. ¿Qué puedo usar para generar la interfaz de usuario con Python?**

R. La oferta principal en este área es [Qt Project](https://www.qt.io/qt-for-application-development/), con enlaces para Python denominados [PySide (el enlace oficial)](http://wiki.qt.io/PySide) (vea también las [descargas de PySide](https://download.qt.io/official_releases/pyside/.)) y [PyQt](https://wiki.python.org/moin/PyQt). En la actualidad, la compatibilidad con Python en Visual Studio no incluye herramientas específicas para el desarrollo de la interfaz de usuario.

**P. ¿Un proyecto de Python puede producir un archivo ejecutable independiente?**

R. Por lo general, Python es un lenguaje interpretado, con código que se ejecuta bajo demanda en un entorno compatible con Python adecuado como Visual Studio y servidores web. En la actualidad, Visual Studio no proporciona por sí mismo los medios para crear un archivo ejecutable independiente, lo que significa básicamente un programa con un intérprete de Python insertado. En cambio, existen varios medios dentro de la comunidad de Python para crear ejecutables como se describe en [StackOverflow](http://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). CPython también se puede insertar en una aplicación nativa, como se describe en la entrada de blog [Using CPython's Embeddable Zip File](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/26/cpython-embeddable-zip-file/) (Uso del archivo Zip insertable de CPython).

## <a name="features-matrix"></a>Matriz de características

La compatibilidad de Python se puede instalar en las siguientes ediciones de Visual Studio, como se describe en la [guía de instalación](installing-python-support-in-visual-studio.md):

- [Visual Studio 2017 (todas las ediciones)](https://www.visualstudio.com/vs/)
- [Visual Studio 2015 (todas las ediciones)] (https://www.visualstudio.com/en-us/downloads/visual-studio-2015-downloads-vs)
- Visual Studio 2013 Community Edition
- Visual Studio 2013 Express para Web, Update 2 o una versión posterior
- Visual Studio 2013 Express para escritorio, Update 2 o una versión posterior
- Visual Studio 2013 (edición Pro o una versión posterior)
- Visual Studio 2012 (edición Pro o una versión posterior)
- Visual Studio 2010 SP1 (edición Pro o una versión posterior; se necesita .NET 4.5)

Características admitidas por la versión y edición de Visual Studio:

| Compatibilidad de Python | 2017 | 2015 | 2013 Comm | 2013 Escritorio | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Administración de varios intérpretes | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
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

- [Puente de WFastCGI entre IIS y Python](https://pypi.python.org/pypi/wfastcgi) (python.org)
- [Cursos gratuitos de Python en Microsoft Virtual Academy](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)
- [Preguntas principales de Python en Microsoft Virtual Academy](https://aka.ms/mva-top-python-questions)
