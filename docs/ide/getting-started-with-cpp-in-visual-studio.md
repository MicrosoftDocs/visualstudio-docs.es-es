---
title: Introducción a C++ en Visual Studio
description: ''
ms.custom: mvc
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
author: corob-msft
ms.author: tglee
manager: douge
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: 65cbfd23c1467988f720822cd68361f5acca23b9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-with-c-in-visual-studio"></a>Introducción a C++ en Visual Studio

Tras completar este inicio rápido, estará familiarizado con muchas de las herramientas y cuadros de diálogo que puede usar para desarrollar aplicaciones en C++ con Visual Studio. Crearemos una aplicación de consola de tipo "Hello, World" mientras aprende más sobre cómo trabajar en el entorno de desarrollo integrado (IDE).

## <a name="prerequisites"></a>Requisitos previos

No es necesario estar familiarizado con C++ para completar este inicio rápido, pero sí conviene estar al tanto de algunos conceptos generales de depuración y programación. La documentación de Visual Studio no sirve para aprender a programar en C++. Una buena guía de recursos de aprendizaje de C++ es la página de [introducción](https://isocpp.org/get-started) del sitio web de ISO C++.

Para seguir este inicio rápido, se necesita una copia de Visual Studio 2017 versión 15.3 o posterior que tenga instalada la carga de trabajo **Desarrollo de escritorio con C++**. Para obtener una guía rápida de instalación, vea [Install C++ support in Visual Studio](/cpp/build/vscpp-step-0-installation) (Instalar la compatibilidad con C++ en Visual Studio).

## <a name="create-a-console-app"></a>Crear una aplicación de consola

Inicie Visual Studio si aún no se está ejecutando.

![IDE con configuración de Visual C&#43;&#43; aplicada](../ide/media/get-started-cpp-ide-layout.png "IDE con configuración de Visual C&#43;&#43; aplicada")

Después de abrir Visual Studio, puede ver las tres partes básicas del IDE: ventanas de herramientas, menús y barras de herramientas, así como el espacio de la ventana principal. Las ventanas de herramientas se acoplan a los lados izquierdo y derecho de la ventana de la aplicación. El cuadro **Inicio rápido**, la barra de menús y la barra de herramientas estándar se sitúan en la parte superior. El centro de la ventana contiene la **Página de inicio**. Cuando se abre una solución o un proyecto, los editores y diseñadores aparecen en este espacio. Al desarrollar una aplicación, la mayor parte del tiempo se invierte en esta área central.

Visual Studio usa *proyectos* para organizar el código de una aplicación y *soluciones* para organizar los proyectos. Un proyecto contiene todas las opciones, las configuraciones y las reglas que se usan para compilar las aplicaciones. También sirve para administrar la relación entre todos los archivos del proyecto y cualquier archivo externo. Para crear la aplicación, hay que crear en primer lugar un proyecto y una solución.

### <a name="to-create-a-console-app-project"></a>Para crear un proyecto de aplicación de consola

1. En la barra de menús, elija **Archivo > Nuevo > Proyecto** para abrir el cuadro de diálogo **Nuevo proyecto**.

   ![En la barra de menús, seleccionamos Archivo > Nuevo > Proyecto](../ide/media/get-started-cpp-file-new-project-menu.png "En la barra de menús, seleccionamos Archivo > Nuevo > Proyecto")

1. En el cuadro de diálogo **Nuevo proyecto**, seleccione **Instalado > Visual C++** si aún no se ha seleccionado. En el panel central, seleccione la plantilla **Aplicación de consola Windows**. En el cuadro de edición **Nombre**, escriba *HelloApp*.

   ![Use el cuadro de diálogo Nuevo proyecto para crear el proyecto de aplicación](../ide/media/get-started-cpp-new-project-dialog.png "Use el cuadro de diálogo Nuevo proyecto para crear el proyecto de aplicación")

   El cuadro de diálogo puede contener opciones diferentes en función de las cargas de trabajo de Visual Studio y los componentes que se hayan instalado. Si no ve las plantillas de proyecto de Visual C++, será necesario volver a ejecutar el Instalador de Visual Studio e instalar la carga de trabajo **Desarrollo de escritorio con C++**. Puede hacerlo directamente desde el cuadro de diálogo **Nuevo proyecto**. Para iniciar el Instalador, seleccione el vínculo **Abrir el instalador de Visual Studio** en el cuadro de diálogo.

1. Seleccione el botón **Aceptar** para crear el proyecto y la solución de la aplicación.

   El proyecto y la solución HelloApp, así como los archivos básicos de una aplicación de consola Windows, se crean y se cargan automáticamente en el **Explorador de soluciones**. El archivo *HelloApp.cpp* se abre en el editor de código. Estos elementos aparecen en el **Explorador de soluciones**:

   ![Archivos de la solución en el Explorador de soluciones](../ide/media/get-started-cpp-solution-explorer.png "Archivos de la solución en el Explorador de soluciones")

## <a name="add-code-to-the-app"></a>Agregar código a la aplicación

El siguiente paso es agregar código para mostrar la palabra "Hello" en la ventana de consola.

### <a name="to-edit-code-in-the-editor"></a>Para editar el código en el editor

1. En el archivo *HelloApp.cpp*, escriba una línea en blanco antes de la línea `return 0;` y, después, escriba este código:

   ```cpp
   cout << "Hello\n";
   ```

   Aparece una línea ondulada roja debajo de `cout`. Si mantiene el puntero sobre ella, aparece un mensaje de error.

   ![Texto de error sobre cout](../ide/media/get-started-cpp-intellisense-error.png "Texto de error sobre cout")

   El mensaje de error también aparece en la ventana **Lista de errores** . Para abrir esta ventana, seleccione **Vista > Lista de errores** en la barra de menús.

   ![Error en la ventana Lista de errores](../ide/media/get-started-cpp-error-list.png "Error en la ventana Lista de errores")

   El código no tiene una declaración para [std::cout](/cpp/standard-library/iostream), que se encuentra en el archivo de encabezado *\<iostream>*.

1. Para incluir el archivo de encabezado de *iostream*, escriba el siguiente código después de `#include "stdafx.h"`:

   ```cpp
   #include <iostream>
   using namespace std;
   ```

   Probablemente haya observado que, al escribir código, ha aparecido un cuadro. Este cuadro contiene sugerencias para completar automáticamente los caracteres a medida que se van escribiendo. Este cuadro forma parte de IntelliSense de C++, que proporciona indicaciones de codificación, incluida información sobre miembros de interfaz o clase y parámetros. También puede usar fragmentos de código, que son bloques de código predefinidos. Para obtener más información, vea [Uso de IntelliSense](../ide/using-intellisense.md) y [Fragmentos de código](../ide/code-snippets.md).

   ![Código corregido en el editor](../ide/media/get-started-cpp-cout-fix.png "Código corregido en el editor")

   La línea ondulada roja bajo `cout` desaparece cuando se corrige el error.

1. Para guardar los cambios en el archivo, presione **CTRL+S**.

## <a name="build-the-app"></a>Compilar la aplicación

El código es fácil de compilar. En la barra de menús, elija **Compilar > Compilar solución**. Visual Studio compila la solución HelloApp e informa del progreso en la ventana **Salida**.

   ![Compilación de la solución HelloApp](../ide/media/get-started-cpp-build-solution.gif "Compilación de la solución HelloApp")

## <a name="debug-and-test-the-app"></a>Depurar y probar la aplicación

Puede depurar HelloApp para ver si aparece la palabra "Hello" en la ventana de consola.

### <a name="to-debug-the-app"></a>Para depurar la aplicación

Para iniciar el depurador, elija **Depurar > Iniciar depuración** en la barra de menús.

![Comando Iniciar depuración en el menú Depurar](../ide/media/get-started-cpp-start-debugging-menu.png "Comando Iniciar depuración en el menú Depurar")

El depurador inicia y ejecuta el código. La ventana de consola (una ventana independiente que se parece a un símbolo del sistema) aparece durante unos segundos, pero se cierra rápidamente cuando el depurador deja de ejecutarse. Para ver el texto, deberá establecer un punto de interrupción para detener la ejecución del programa.

### <a name="to-add-a-breakpoint"></a>Para agregar un punto de interrupción

1. En el editor, coloque el cursor sobre la línea `return 0;`. En la barra de menús, elija **Depurar > Alternar punto de interrupción**. También puede hacer clic en el margen izquierdo para establecer un punto de interrupción.

     ![Comando Alternar punto de interrupción en el menú Depurar](../ide/media/get-started-cpp-toggle-breakpoint-menu.png "Comando Alternar punto de interrupción en el menú Depurar")

     Aparece un círculo rojo al lado de la línea de código en el margen izquierdo de la ventana del editor.

     ![Punto de interrupción señalado en el margen de la ventana](../ide/media/get-started-cpp-breakpoint-set.png "Punto de interrupción señalado en el margen de la ventana")

1. Presione **F5** para iniciar la depuración.

   El depurador se inicia y aparece una ventana de consola con la palabra **Hola**.

   ![Texto Hello en la ventana de consola](../ide/media/get-started-cpp-helloapp-window.png "Texto Hello en la ventana de consola")

1. Presione **MAYÚS+F5** para detener la depuración.

Para más información sobre la depuración de proyectos de consola, vea [Proyectos de consola](../debugger/debugging-preparation-console-projects.md).

## <a name="build-a-release-version-of-the-app"></a>Compilar una versión de lanzamiento de la aplicación

Ahora que ha comprobado que todo funciona, puede preparar una versión de lanzamiento de la aplicación. Las versiones de lanzamiento prescinden de la información de depuración y usan opciones de optimización de compilador para crear un código más breve y rápido.

### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Para limpiar los archivos de solución y crear una versión de lanzamiento

1. En la barra de menús, elija **Compilar > Limpiar solución** para eliminar los archivos intermedios y de salida que se han creado durante las compilaciones anteriores.

   ![El comando Limpiar solución del menú Compilar](../ide/media/get-started-cpp-clean-solution-menu.png "ExploreIDE-CleanSolution")

1. Para cambiar la configuración de solución de HelloApp de **Debug** a **Release**, en la barra de herramientas, seleccione la lista desplegable del control Configuraciones de soluciones y, después, elija **Release**.

   ![Compilar una versión de lanzamiento de la aplicación](../ide/media/get-started-cpp-set-release-configuration.png "C++IDE_ChangingBuildtoRelease")

1. Compile la solución. En la barra de menús, elija **Compilar > Compilar solución**.

Cuando esta compilación acabe, habrá creado una aplicación que se puede copiar y ejecutar en cualquier ventana de símbolo del sistema. Puede que no sea mucho, pero abre la puerta a cosas mucho más grandes.

¡Enhorabuena por completar este tutorial de inicio rápido! Si desea explorar más ejemplos, vea [ejemplos de Visual Studio](../ide/visual-studio-samples.md).

## <a name="see-also"></a>Vea también

- [Usar el IDE de Visual Studio para desarrollo de escritorio de C++](/cpp/ide/using-the-visual-studio-ide-for-cpp-desktop-development)
- [Tutorial: Creación de una aplicación sencilla con C# o Visual Basic](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)
- [Sugerencias de productividad para Visual Studio](../ide/productivity-tips-for-visual-studio.md)
- [Ejemplos de Visual Studio](../ide/visual-studio-samples.md)
- [Introducción al desarrollo con Visual Studio](../ide/get-started-developing-with-visual-studio.md)
