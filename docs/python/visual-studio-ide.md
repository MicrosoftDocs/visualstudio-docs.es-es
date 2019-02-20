---
title: Información general de Visual Studio para desarrolladores de Python
titleSuffix: ''
ms.date: 12/14/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
dev_langs:
- Python
ms.workload:
- python
- data-science
ms.openlocfilehash: 094a768f0b1b50e03bb445becb956e8e91a862da
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "56316618"
---
# <a name="welcome-to-the-visual-studio-ide--python"></a>Bienvenida al IDE de Visual Studio | Python

El *entorno de desarrollo integrado* de Visual Studio es un panel de inicio creativo para Python (y otros lenguajes) que se puede usar para editar, depurar y probar código y, después, publicar una aplicación. Un entorno de desarrollo integrado (IDE) es un programa con numerosas características que se pueden usar para muchos aspectos del desarrollo de software. Más allá del editor estándar y el depurador que proporcionan la mayoría de IDE, Visual Studio incluye herramientas de finalización de código, entornos de REPL interactivos y otras características para facilitar el proceso de desarrollo de software.

[![Visual Studio con un proyecto de Python](media/tour-ide-overview.png)](media/tour-ide-overview.png#lightbox)

En esta imagen se muestra Visual Studio con un proyecto de Python abierto y varias ventanas de herramientas clave que probablemente usará:

- El [**Explorador de soluciones**](../ide/solutions-and-projects-in-visual-studio.md) (parte superior derecha) permite ver, desplazarse por y administrar los archivos de código. El **Explorador de soluciones** puede ayudar a organizar el código al agrupar los archivos en [soluciones y proyectos](/visualstudio/get-started/tutorial-projects-solutions).
    - Además del **Explorador de soluciones**, están los [**entornos de Python**](managing-python-environments-in-visual-studio.md), donde se administran los diferentes intérpretes de Python que hay instalados en el equipo.

- La [ventana del editor](../ide/writing-code-in-the-code-and-text-editor.md) (centro), donde es probable que pase la mayor parte del tiempo, muestra el contenido del archivo. Aquí es donde se [edita código de Python](editing-python-code-in-visual-studio.md), se navega por la estructura del código y se establecen puntos de interrupción durante las sesiones de depuración. Con Python, también puede seleccionar código y presionar Ctrl+ENTRAR para ejecutar ese código en una [ventana de REPL interactiva](python-interactive-repl-in-visual-studio.md).

- La [ventana Resultados](../ide/reference/output-window.md) (parte inferior central) es donde Visual Studio envía notificaciones, como mensajes de error y de depuración, advertencias, mensajes de estado de publicación, etc. Cada código fuente de mensaje tiene su propia pestaña.
    - Una [ventana de REPL interactiva de Python](python-interactive-repl-in-visual-studio.md) aparece en la misma área que la ventana Resultados.

- [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts) (parte inferior derecha) permite realizar el seguimiento de los elementos de trabajo y compartir código con otros usuarios mediante tecnologías de control de versiones como [Git](https://git-scm.com/) y [Control de versiones de Team Foundation (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts).

## <a name="editions"></a>Ediciones

Visual Studio está disponible para Windows y Mac, pero Python solo es compatible con Visual Studio para Windows.

Existen tres ediciones de Visual Studio 2017 en Windows: Community, Professional y Enterprise. Vea [Comparar los IDE de Visual Studio 2017](https://visualstudio.microsoft.com/vs/compare/) para obtener información sobre las características que se admiten en cada edición.

## <a name="popular-productivity-features"></a>Características de productividad populares

Algunas de las características populares de Visual Studio que ayudan a ser más productivos durante el desarrollo de software incluyen:

- [IntelliSense](editing-python-code-in-visual-studio.md#intellisense)

   IntelliSense es un término que define un conjunto de características que muestran información sobre el código directamente en el editor y, en algunos casos, escriben pequeños fragmentos de código automáticamente. Es como tener documentación básica insertada en el editor, lo que evita tener que buscar información escrita en cualquier otro lugar. Las características de IntelliSense varían según el lenguaje. En el artículo [Editar código de Python](editing-python-code-in-visual-studio.md#intellisense) encontrará los detalles relativos a Python. La siguiente ilustración muestra cómo IntelliSense muestra una lista de miembros de un tipo:

   ![Finalización de miembros con IntelliSense de Visual Studio](media/code-editing-completions-simple.png)

- [Refactorización](refactoring-python-code.md)

   Si hacemos clic con el botón derecho en un fragmento de código y seleccionamos **Acciones rápidas y refactorizaciones**, Visual Studio proporciona operaciones como el cambio inteligente de nombres de variables, la extracción de una o más líneas de código en un nuevo método, el cambio del orden de los parámetros de método, etc.

   ![Refactorización en Visual Studio](media/tour-ide-refactor-extract-method.png)

- [Detección de errores](refactoring-python-code.md)

   La detección de errores comprueba si hay errores y problemas comunes en el código de Python, lo cual fomenta un uso adecuado de patrones de codificación de Python.

   ![Comando PyLint en el menú contextual para proyectos de Python](media/code-pylint-command.png)

- [Inicio rápido](../ide/reference/quick-launch-environment-options-dialog-box.md)

   Visual Studio puede parecer abrumador a veces con tantas propiedades, opciones y menús. El cuadro de búsqueda **Inicio rápido** supone una excelente manera de encontrar rápidamente lo que necesita en Visual Studio. Al empezar a escribir el nombre de lo que está buscando, Visual Studio muestra resultados que llevan exactamente a donde necesita ir. Si necesita agregar funcionalidad a Visual Studio, por ejemplo, agregar compatibilidad con otro lenguaje de programación, **Inicio rápido** proporciona resultados que abren el Instalador de Visual Studio para instalar un componente individual o una carga de trabajo.

   ![Cuadro de búsqueda Inicio rápido en Visual Studio](media/tour-ide-quick-launch.png)

- Subrayados ondulados y [Acciones rápidas](../ide/quick-actions.md)

   Los subrayados ondulados son rayas con formas de onda debajo de las palabras que alertan de errores o posibles problemas en el código a medida que se escribe. Estas pistas visuales permiten corregir problemas inmediatamente sin esperar a que el error se detecte durante la compilación o cuando se ejecute el programa. Si mantiene el cursor sobre un subrayado ondulado, se ve información adicional sobre el error. También puede aparecer una bombilla en el margen izquierdo con acciones, conocidas como Acciones rápidas, para corregir el error.

   ![Subrayados ondulados en Visual Studio](media/tour-ide-squiggles.png)

- [Ir a la definición y verla](../ide/go-to-and-peek-definition.md)

   La característica **Ir a definición** lleva directamente a la ubicación donde se define una función o un tipo. El comando **Ver la definición** muestra la definición en una ventana, sin tener que abrir un archivo aparte. El comando **Buscar todas las referencias** es igualmente una forma útil de detectar aquellas instancias en las que un identificador determinado se define y utiliza.

   ![Comandos de navegación por el código](media/tour-ide-navigation-commands.png)

## <a name="powerful-features-for-python"></a>Características eficaces de Python

- [Ventana de REPL interactiva](python-interactive-repl-in-visual-studio.md)

    Visual Studio proporciona una ventana interactiva read-evaluate-print loop (REPL) para cada entorno de Python, que ofrece mejoras con respecto al REPL obtenido con *python.exe* en la línea de comandos. En la ventana **Interactiva** puede escribir código de Python arbitrario y ver resultados inmediatos.

    ![Ventana interactiva de Python](media/interactive-window.png)

- [Depuración](debugging-python-in-visual-studio.md)

    Visual Studio proporciona una experiencia de depuración completa para Python, lo que incluye la asociación a procesos en ejecución, la evaluación de expresiones en las ventanas **Inspección** e **Inmediato**, la inspección de variables locales, los puntos de interrupción, las instrucciones Depurar paso a paso por instrucciones/procedimientos/para salir, **Establecer instrucción siguiente**, etc. También puede depurar código de Python remoto que se ejecuta en equipos Linux.

    ![Depuración de Python en Visual Studio](media/remote-debugging-breakpoint-hit.png)

- [Interacción con C++](working-with-c-cpp-python-in-visual-studio.md)

    Muchas de las bibliotecas creadas para Python están escritas en C++ para lograr el mejor rendimiento posible. Visual Studio proporciona funcionalidades muy completas para desarrollar extensiones de C++, incluida la [depuración en modo mixto](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

    ![Depuración conjunta en modo mixto de Python y C++](media/mixed-mode-debugging.png)

- [Generación de perfiles](profiling-python-code-in-visual-studio.md)

    Cuando se usa un intérprete basado en CPython, se puede evaluar el rendimiento del código de Python en Visual Studio.

    ![Informe de rendimiento de generación de perfiles](media/profiling-results.png)

- [Pruebas unitarias](unit-testing-python-in-visual-studio.md)

    Visual Studio proporciona compatibilidad integrada para detectar, ejecutar y depurar pruebas unitarias en el contexto del IDE.

    ![Pruebas de unidades con un estado de prueba no superada](media/unit-test-A-fail.png)

## <a name="next-steps"></a>Pasos siguientes

Continúe explorando Python en Visual Studio siguiendo uno de los siguientes tutoriales o inicios rápidos:

> [!div class="nextstepaction"]
> [Inicio rápido: Crear una aplicación web con Flask](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)

> [!div class="nextstepaction"]
> [Uso de Python en Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

> [!div class="nextstepaction"]
> [Introducción al marco web de Django en Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)

> [!div class="nextstepaction"]
> [Introducción al marco web Flask en Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)

## <a name="see-also"></a>Vea también

- Descubra [más características de Visual Studio](../ide/advanced-feature-overview.md)
- Visite [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/)
- Lea el [blog de Visual Studio](https://devblogs.microsoft.com/visualstudio/)