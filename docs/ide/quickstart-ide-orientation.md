---
title: Paseo por el IDE de Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/15/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a74d123d8cb0055f01619bae25b9a1bda54b35f4
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2018
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Guía de inicio rápido: primer vistazo al IDE de Visual Studio

En esta introducción al entorno de desarrollo integrado (IDE) de Visual Studio, de 5 a 10 minutos de duración, pasaremos por algunas de las ventanas, menús y otras funciones de la interfaz de usuario.

## <a name="start-page"></a>Página de inicio

Probablemente lo primero que vea después de iniciar Visual Studio sea la página de inicio. La página de inicio está diseñada como un "concentrador" que le ayudará a encontrar los comandos y archivos de proyecto que necesita más rápidamente. La sección **Recientes** muestra los proyectos y las carpetas en las que ha trabajado recientemente. En **Nuevo proyecto**, puede hacer clic en un vínculo para abrir el cuadro de diálogo Nuevo proyecto o, en **Abrir**, puede abrir una carpeta de código o proyecto existente. A la derecha hay una fuente con las últimas noticias del desarrollador.

![Página de inicio de Visual Studio](media/quickstart-IDE-start-page.png)

Si cierra la página de inicio y desea verla de nuevo, puede volver a abrirla desde el menú **Archivo**.

![menú Archivo](media/quickstart-IDE-file-menu-large.png)

Para seguir explorando el IDE, se va a crear un nuevo proyecto.

1. En la **Página de inicio**, en el cuadro de búsqueda en **Nuevo proyecto**, escriba `console` para filtrar la lista de tipos de proyecto. Elija **Console App (.NET Framework)** de C# o Visual Studio. (Además, si es un desarrollador de C++, Javascript u otro lenguaje, no dude en crear un proyecto en uno de esos lenguajes. La interfaz de usuario que se muestra es similar para todos los lenguajes).

1. En el cuadro de diálogo **Nuevo proyecto**, acepte el nombre del proyecto predeterminado y elija **Aceptar**.

   Se crea el proyecto y se abre un archivo llamado **Program. cs** o **Program. vb** en la ventana **Editor**. El editor muestra el contenido de los archivos y es allí donde se va a realizar la mayor parte del trabajo de codificación en Visual Studio.

## <a name="solution-explorer"></a>Explorador de soluciones

El Explorador de soluciones muestra una representación gráfica de la jerarquía de archivos y en el proyecto, solución o carpeta de código. Puede examinar la jerarquía y navegar hasta un archivo en el Explorador de soluciones.

![Explorador de soluciones](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menús

La barra de menús en la parte superior del IDE agrupa los comandos en categorías. Por ejemplo, el menú **Proyecto** contiene comandos relacionados con el proyecto en el que está trabajando. En el menú **Herramientas**, puede personalizar el IDE mediante la selección de **Opciones** o agregar características a la instalación mediante la selección de **Obtener herramientas y características...**

![Barra de menús](media/quickstart-IDE-menu-bar.png)

Se abre la ventana Lista de errores mediante la selección del menú **Ver** y después **Lista de errores**.

## <a name="error-list"></a>Lista de errores

La lista de errores muestra los errores, las advertencias y los mensajes relacionados con el estado actual del código. Si se produjera algún error (como un error de sintaxis) en el archivo, o en cualquier parte del proyecto, se enumeraría aquí.

![Lista de errores](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Resultados (ventana)

La ventana de salida muestra los mensajes de salida de Compilación y Control de código fuente.

Vamos a compilar el proyecto para ver algún registro de salida. En el menú **Compilar** , elija **Compilar solución**. La ventana de salida obtiene automáticamente el foco y muestra un mensaje de compilación realizada correctamente.

![Resultados (Ventana)](media/quickstart-IDE-output.png)

## <a name="quick-launch"></a>Inicio rápido

El cuadro Inicio rápido es una manera rápida y sencilla que hacer prácticamente todo en el IDE. Puede especificar algún texto relacionado con lo que quiere hacer, y se mostrará una lista de opciones que pertenecen al texto. Por ejemplo, supongamos que se quiere aumentar el detalle de la salida de compilación para mostrar información de registro adicional sobre lo que está haciendo exactamente la compilación:

1. Escriba `verbosity` en el cuadro **Inicio rápido** y, después, seleccione **Proyectos y soluciones -> Compilar y ejecutar** en la categoría **Opciones**.

   ![Cuadro Inicio rápido](media/quickstart-IDE-quick-launch.png)

   El cuadro de diálogo **Opciones** se abre en la página **Compilar y ejecutar**.

1. En **Detalles de la salida de la compilación del proyecto de MSBuild**, elija **Normal** y después haga clic en **Aceptar**.

1. Ahora se va a volver a compilar el proyecto haciendo clic con el botón derecho en **ConsoleApp1** en el **Explorador de soluciones** y seleccionando **Recompilar** en el menú contextual.

   Esta vez la ventana de salida muestra un registro más detallado del proceso de compilación, incluso en dónde se copiaron los archivos.

## <a name="send-feedback-menu"></a>Menú Enviar comentarios

Si encuentra algún problema durante el uso de Visual Studio, o si tiene sugerencias para mejorar el producto, puede utilizar el menú **Enviar comentarios** en la parte superior del IDE, junto al cuadro Inicio rápido.

![Menú Enviar comentarios](media/quickstart-IDE-send-feedback.png)

## <a name="next-steps"></a>Pasos siguientes

Hemos examinado solo algunas de las características del IDE de Visual Studio para familiarizarnos con la interfaz de usuario. Para explorarla más a fondo:

- Busque la sección Elementos de la interfaz de usuario general de la documentación de Visual Studio, que profundiza en las ventanas como [Lista de errores](../ide/reference/error-list-window.md), [Ventana de salida](../ide/reference/output-window.md), [Ventana Propiedades](../ide/reference/properties-window.md) y [Cuadro de diálogo Opciones](../ide/reference/options-dialog-box-visual-studio.md).

- Adéntrese aún más en el IDE e incluso incursione en la depuración, en [Introducción al IDE de Visual Studio](../ide/visual-studio-ide.md).

## <a name="see-also"></a>Vea también

[Guía de inicio rápido: personalización del IDE](../ide/personalizing-the-visual-studio-ide.md)  
[Inicio rápido: escritura de código en el editor](../ide/quickstart-editor.md)  
[Inicio rápido: proyectos y soluciones](../ide/quickstart-projects-solutions.md)