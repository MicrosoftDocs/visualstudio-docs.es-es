---
title: Un paseo por el IDE de Visual Studio
ms.date: 07/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 249ea0c20bc47f63999a08962ba6cf7d1effd2b1
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513278"
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Guía de inicio rápido: primer vistazo al IDE de Visual Studio

En esta introducción al entorno de desarrollo integrado (IDE) de Visual Studio, de 5 a 10 minutos de duración, pasaremos por algunas de las ventanas, menús y otras funciones de la interfaz de usuario.

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalarlo de forma gratuita.

## <a name="start-page"></a>Página de inicio

Probablemente lo primero que verá después de iniciar Visual Studio sea la **página de inicio**. La **página de inicio** está diseñada como un "concentrador" para ayudarle a encontrar los comandos y archivos de proyecto que necesita más rápidamente. La sección **Recientes** muestra los proyectos y las carpetas en las que ha trabajado recientemente. En **Nuevo proyecto**, puede hacer clic en un vínculo para abrir el cuadro de diálogo **Nuevo proyecto** o bien en **Abrir** para abrir un proyecto o una carpeta de código existentes. A la derecha hay una fuente con las últimas noticias del desarrollador.

![Página de inicio en Visual Studio](media/start-page.png)

Si cierra la **página de inicio** y quiere verla de nuevo, puede volver a abrirla desde el menú **Archivo**.

![Menú Archivo en Visual Studio](media/quickstart-IDE-file-menu-large.png)

## <a name="create-a-project"></a>Crear un proyecto

Para seguir examinando las características de Visual Studio, se va a crear un nuevo proyecto.

1. En la **página de inicio**, en el cuadro de búsqueda de **Nuevo proyecto**, escriba **console** para filtrar la lista de tipos de proyecto a los que contengan "console" en su nombre.

   ![Búsqueda de plantillas de proyecto en la página de inicio de Visual Studio](media/start-page-search-templates.png)

   Visual Studio proporciona varios tipos de plantillas de proyecto que ayudan a comenzar a codificar rápidamente. Elija una plantilla de proyecto **Console App (.NET Framework)** de C#. (Si es desarrollador de Visual Basic, C++, Javascript u otro lenguaje, también puede crear un proyecto en uno de esos lenguajes. La interfaz de usuario que se muestra es similar para todos los lenguajes de programación).

1. En el cuadro de diálogo **Nuevo proyecto** que aparece, acepte el nombre de proyecto predeterminado y haga clic en **Aceptar**.

   Se crea el proyecto y se abre un archivo denominado *Program.cs* en la ventana **Editor**. En el **Editor** se muestra el contenido de los archivos y es donde se va a realizar la mayor parte del trabajo de codificación en Visual Studio.

   ![Editor en Visual Studio](media/editor.png)

## <a name="solution-explorer"></a>Explorador de soluciones

En el **Explorador de soluciones**, que normalmente se encuentra en el lado derecho de Visual Studio, se muestra una representación gráfica de la jerarquía de los archivos y las carpetas del proyecto, la solución o la carpeta de código. En el **Explorador de soluciones** se puede examinar la jerarquía y navegar hasta un archivo.

![Explorador de soluciones en Visual Studio](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menús

La barra de menús de la parte superior de Visual Studio agrupa los comandos en categorías. Por ejemplo, el menú **Proyecto** contiene comandos relacionados con el proyecto en el que está trabajando. En el menú **Herramientas**, se puede personalizar el comportamiento de Visual Studio mediante la selección de **Opciones**, o bien agregar características a la instalación mediante la selección de **Obtener herramientas y características**.

![Barra de menús en Visual Studio](media/quickstart-IDE-menu-bar.png)

Se abre la ventana **Lista de errores** mediante la selección del menú **Ver** y después **Lista de errores**.

## <a name="error-list"></a>Lista de errores

En la **Lista de errores** se muestran los errores, las advertencias y los mensajes relacionados con el estado actual del código. Si se produjera algún error (por ejemplo, la falta de un paréntesis o un punto y coma) en el archivo o en cualquier parte del proyecto, se indicaría aquí.

![Lista de errores en Visual Studio](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Resultados (ventana)

En la ventana **Resultados** se muestran los mensajes de resultados de la compilación del proyecto y del proveedor de control de código fuente.

Vamos a compilar el proyecto para ver algún resultado de compilación. En el menú **Compilar** , elija **Compilar solución**. La ventana **Resultados** obtiene automáticamente el foco y muestra un mensaje de compilación correcta.

![Ventana Resultados en Visual Studio](media/build-output-minimal.png)

## <a name="quick-launch"></a>Inicio rápido

El cuadro **Inicio rápido** es una manera rápida y sencilla de hacer prácticamente todo en Visual Studio. Puede especificar algún texto relacionado con lo que quiere hacer, y se mostrará una lista de opciones que pertenecen al texto. Por ejemplo, supongamos que se quiere aumentar el detalle de los resultados de compilación para mostrar más detalles sobre lo que está haciendo exactamente la compilación. Así es como se haría:

1. Escriba **verbosity** en el cuadro **Inicio rápido**. En los resultados que aparecen, elija **Proyectos y soluciones --> Compilar y ejecutar** en la categoría **Opciones**.

   ![Cuadro Inicio rápido en Visual Studio](media/quickstart-IDE-quick-launch.png)

   El cuadro de diálogo **Opciones** se abre en la página **Compilar y ejecutar**.

1. En **Detalles de la salida de la compilación del proyecto de MSBuild**, elija **Normal** y después haga clic en **Aceptar**.

1. Vuelva a compilar el proyecto al hacer clic con el botón derecho en el proyecto **ConsoleApp1** del **Explorador de soluciones** y elija **Recompilar** en el menú contextual.

   Esta vez, en la ventana **Resultados** se muestra un registro más detallado del proceso de compilación, incluido dónde se copiaron los archivos.

   ![Resultados de compilación detallados en Visual Studio](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>Menú Enviar comentarios

Si encuentra algún problema mientras usa Visual Studio o si tiene sugerencias para mejorar el producto, puede usar el menú **Enviar comentarios** de la parte superior de la ventana de Visual Studio, junto al cuadro **Inicio rápido**.

![Menú Enviar comentarios en Visual Studio](media/quickstart-IDE-send-feedback.png)

## <a name="next-steps"></a>Pasos siguientes

Solo se han examinado algunas de las características de Visual Studio para familiarizarse con la interfaz de usuario. Para explorarla más a fondo:

> [!div class="nextstepaction"]
> [Guía de inicio rápido: personalización del IDE](../ide/quickstart-personalize-the-ide.md)

> [!div class="nextstepaction"]
> [Inicio rápido: Escribir código en el editor](../ide/quickstart-editor.md)

> [!div class="nextstepaction"]
> [Inicio rápido: proyectos y soluciones](../ide/quickstart-projects-solutions.md)

## <a name="see-also"></a>Vea también

- [Información general sobre Visual Studio](../ide/visual-studio-ide.md)
- [Características de Visual Studio 2017](../ide/advanced-feature-overview.md)