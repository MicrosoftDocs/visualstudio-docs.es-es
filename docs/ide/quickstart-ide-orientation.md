---
title: Un paseo por el IDE de Visual Studio
titleSuffix: ''
ms.date: 02/21/2019
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 490d3edddd35ad5d72733824e3af41888839e946
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596975"
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Inicio rápido: Primer vistazo al IDE de Visual Studio

En esta introducción al entorno de desarrollo integrado (IDE) de Visual Studio, de 5 a 10 minutos de duración, pasaremos por algunas de las ventanas, menús y otras funciones de la interfaz de usuario.

::: moniker range="vs-2017"

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) para instalarlo de forma gratuita.

::: moniker-end

::: moniker range=">=vs-2019"

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads) para instalarlo de forma gratuita.

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>Página de inicio

Probablemente lo primero que verá después de abrir Visual Studio sea la **página de inicio**. La **página de inicio** está diseñada como un "concentrador" para ayudarle a encontrar los comandos y archivos de proyecto que necesita más rápidamente. La sección **Recientes** muestra los proyectos y las carpetas en las que ha trabajado recientemente. En **Nuevo proyecto**, puede hacer clic en un vínculo para abrir el cuadro de diálogo **Nuevo proyecto** o bien en **Abrir** para abrir un proyecto o una carpeta de código existentes. A la derecha hay una fuente con las últimas noticias del desarrollador.

![Página de inicio en Visual Studio](media/start-page.png)

Si cierra la **página de inicio** y quiere verla de nuevo, puede volver a abrirla desde el menú **Archivo**.

![Menú Archivo en Visual Studio](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a>Ventana de inicio

Lo primero que se ve al abrir Visual Studio es la ventana de inicio. La ventana de inicio está concebida para ayudar a "obtener código" más rápido. Tiene opciones para clonar o desproteger código, abrir una solución o un proyecto existente, crear un nuevo proyecto o simplemente abrir una carpeta que contiene algunos archivos de código.

[![Ventana de inicio de Visual Studio 2019](media/vs-2019/start-window-labeled.png)](media/vs-2019/start-window-labeled.png#lightbox)

Si es la primera vez que se usa Visual Studio, la lista de proyectos recientes está vacía.

Si se trabaja con código base no basado en MSBuild, se usa la opción **Abrir una carpeta local** para abrir el código en Visual Studio. Para obtener más información, vea [Desarrollo de código en Visual Studio sin proyectos o soluciones](develop-code-in-visual-studio-without-projects-or-solutions.md). De lo contrario, se puede crear un nuevo proyecto o clonar un proyecto de un proveedor de origen como GitHub o Azure DevOps.

La opción **Continuar sin código** simplemente abre el entorno de desarrollo de Visual Studio sin ningún proyecto o código concreto cargado. Puede elegir esta opción para unir a una sesión de [Live Share](/visualstudio/liveshare/) o asociar a un proceso para la depuración. También puede presionar **Esc** para cerrar la ventana de inicio y abrir el IDE.

::: moniker-end

## <a name="create-a-project"></a>Crear un proyecto

Para seguir examinando las características de Visual Studio, se va a crear un nuevo proyecto.

::: moniker range="vs-2017"

1. En la **página de inicio**, en el cuadro de búsqueda de **Nuevo proyecto**, escriba **console** para filtrar la lista de tipos de proyecto a los que contengan "console" en su nombre.

   ![Búsqueda de plantillas de proyecto en la página de inicio de Visual Studio](media/start-page-search-templates.png)

   Visual Studio proporciona varios tipos de plantillas de proyecto que ayudan a comenzar a codificar rápidamente. Elija una plantilla del proyecto **Aplicación de consola (.NET Core)** en C#. (Si es desarrollador de Visual Basic, C++, Javascript u otro lenguaje, también puede crear un proyecto en uno de esos lenguajes. La interfaz de usuario que se muestra es similar para todos los lenguajes de programación).

1. En el cuadro de diálogo **Nuevo proyecto** que aparece, acepte el nombre de proyecto predeterminado y haga clic en **Aceptar**.

::: moniker-end

::: moniker range=">=vs-2019"

1. En la ventana de inicio, elija **Crear un proyecto nuevo**.

   Se abre un cuadro de diálogo de nombre **Crear un proyecto**. Aquí, puede buscar, filtrar y seleccionar una plantilla de proyecto. También muestra una lista de las plantillas de proyecto recientemente usadas.

1. En el cuadro de búsqueda superior, escriba **consola** para filtrar la lista de tipos de proyecto a solo los que incluyen "consola" en el nombre. Para refinar los resultados de la búsqueda, elija **C#** (u otro lenguaje que prefiera) en el selector de **Lenguaje**.

   ![Cuadro de diálogo Nuevo proyecto de Visual Studio 2019](media/vs-2019/create-a-new-project.png)

1. Si seleccionó C#, Visual Basic o F# como lenguaje, seleccione la plantilla **Aplicación de consola (.NET Framework)** y, luego, elija **Siguiente**. (Si seleccionó otro lenguaje, elija cualquier plantilla. La interfaz de usuario que se muestra es similar para todos los lenguajes de programación).

1. En la página **Configure su nuevo proyecto**, acepte el nombre y la ubicación predeterminados del proyecto y haga clic en **Crear**.

::: moniker-end

   Se crea el proyecto y se abre un archivo denominado *Program.cs* en la ventana **Editor**. En el **Editor** se muestra el contenido de los archivos y es donde se va a realizar la mayor parte del trabajo de codificación en Visual Studio.

   ![Editor en Visual Studio](media/editor.png)

## <a name="solution-explorer"></a>Explorador de soluciones

En el **Explorador de soluciones**, que normalmente se encuentra en el lado derecho de Visual Studio, se muestra una representación gráfica de la jerarquía de los archivos y las carpetas del proyecto, la solución o la carpeta de código. En el **Explorador de soluciones** se puede examinar la jerarquía y navegar hasta un archivo.

![Explorador de soluciones en Visual Studio](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menús

La barra de menús de la parte superior de Visual Studio agrupa los comandos en categorías. Por ejemplo, el menú **Proyecto** contiene comandos relacionados con el proyecto en el que está trabajando. En el menú **Herramientas**, se puede personalizar el comportamiento de Visual Studio mediante la selección de **Opciones**, o bien agregar características a la instalación mediante la selección de **Obtener herramientas y características**.

::: moniker range="vs-2017"

![Barra de menús de Visual Studio 2017](media/quickstart-IDE-menu-bar.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Barra de menús de Visual Studio 2019](media/vs-2019/menu-bar.png)

::: moniker-end

## <a name="error-list"></a>Lista de errores

Abra la ventana **Lista de errores** mediante la selección del menú **Ver** y después **Lista de errores**.

En la **Lista de errores** se muestran los errores, las advertencias y los mensajes relacionados con el estado actual del código. Si se produjera algún error (por ejemplo, la falta de un paréntesis o un punto y coma) en el archivo o en cualquier parte del proyecto, se indicaría aquí.

![Lista de errores en Visual Studio](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Resultados (ventana)

En la ventana **Resultados** se muestran los mensajes de resultados de la compilación del proyecto y del proveedor de control de código fuente.

Vamos a compilar el proyecto para ver algún resultado de compilación. En el menú **Compilar** , elija **Compilar solución**. La ventana **Resultados** obtiene automáticamente el foco y muestra un mensaje de compilación correcta.

![Ventana Resultados en Visual Studio](media/build-output-minimal.png)

## <a name="search-box"></a>Cuadro de búsqueda

El cuadro de búsqueda es una manera rápida y sencilla de navegar prácticamente por todo en Visual Studio. Puede especificar algún texto relacionado con lo que quiere hacer, y se mostrará una lista de opciones que pertenecen al texto. Por ejemplo, supongamos que se quiere aumentar el detalle de los resultados de compilación para mostrar más detalles sobre lo que está haciendo exactamente la compilación. Así es como se haría:

::: moniker range="vs-2017"

1. Localice el cuadro de búsqueda **Inicio rápido** en la esquina superior derecha del IDE. (Como alternativa, presione **Ctrl**+**Q** para acceder a él).

2. Escriba **detalle** en el cuadro de búsqueda. En los resultados que aparecen, elija **Proyectos y soluciones --> Compilar y ejecutar** en la categoría **Opciones**.

   ![Cuadro de búsqueda Inicio rápido en Visual Studio 2017](media/quickstart-IDE-quick-launch.png)

   El cuadro de diálogo **Opciones** se abre en la página **Compilar y ejecutar**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Presione **Ctrl**+**Q** para activar el cuadro de búsqueda en la parte superior del IDE.

2. Escriba **nivel de detalle** en el cuadro de búsqueda. En los resultados que se muestran, elija **Change MSBuild verbosity** (Cambiar el nivel de detalle de MSBuild).

   ![Cuadro de búsqueda de Visual Studio 2019](media/vs-2019/quick-launch-verbosity.png)

   El cuadro de diálogo **Opciones** se abre en la página **Compilar y ejecutar**.

::: moniker-end

3. En **Detalles de la salida de la compilación del proyecto de MSBuild**, elija **Normal** y después haga clic en **Aceptar**.

4. Vuelva a compilar el proyecto al hacer clic con el botón derecho en el proyecto **ConsoleApp1** del **Explorador de soluciones** y elija **Recompilar** en el menú contextual.

   Esta vez, en la ventana **Resultados** se muestra un registro más detallado del proceso de compilación, incluido dónde se copiaron los archivos.

   ![Resultados de compilación detallados en Visual Studio](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Menú Enviar comentarios

Si encuentra algún problema mientras usa Visual Studio o si tiene sugerencias para mejorar el producto, puede usar el menú **Enviar comentarios** de la parte superior de la ventana de Visual Studio.

::: moniker range="vs-2017"

![Menú Enviar comentarios de Visual Studio 2017](media/quickstart-IDE-send-feedback.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Menú Enviar comentarios de Visual Studio 2019](media/vs-2019/send-feedback-menu.png)

::: moniker-end

## <a name="next-steps"></a>Pasos siguientes

Solo se han examinado algunas de las características de Visual Studio para familiarizarse con la interfaz de usuario. Para explorarla más a fondo:

> [!div class="nextstepaction"]
> [Acerca del editor de código](../get-started/tutorial-editor.md)

> [!div class="nextstepaction"]
> [Información sobre proyectos y soluciones](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Vea también

- [Información general sobre Visual Studio](../get-started/visual-studio-ide.md)
- [Más características de Visual Studio](../ide/advanced-feature-overview.md)
- [Cambiar los colores de la fuente y el tema](../ide/quickstart-personalize-the-ide.md)
