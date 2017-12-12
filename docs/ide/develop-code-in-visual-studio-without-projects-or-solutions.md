---
title: "Desarrollo de código en Visual Studio sin proyectos o soluciones | Microsoft Docs"
ms.custom: 
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.texteditor
dev_langs:
- JScript
- VB
- CSharp
helpviewer_keywords:
- code, editing
- code editor, syntax coloring
- code editor [Visual Studio]
- brace matching
- code editor, line numbers
- code editor, brace matching
- line numbers
- syntax coloring
- code editor
- code files
- code
ms.assetid: cb53bb9b-5b76-4759-b9b8-7bf32298bcbb
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e9531a49ced6e8f72154cbdd59fce271ff673f59
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="develop-code-in-visual-studio-without-projects-or-solutions"></a>Desarrollo de código en Visual Studio sin proyectos o soluciones  
En Visual Studio 2017, puede abrir código desde casi cualquier tipo de proyecto basado en directorios en Visual Studio sin necesidad de un archivo de solución o proyecto. Esto significa que, por ejemplo, puede buscar un proyecto de código en Git, clonarlo y, después, abrirlo directamente en Visual Studio y comenzar a desarrollar sin tener que crear una solución o proyecto.  

No solo puede modificar el código y compilarlo en Visual Studio, sino que también puede desplazarse por el código (por ejemplo mediante el comando Navegar a). El código aparecerá con coloración de sintaxis y, en muchos casos, incluirá la finalización de instrucciones básicas y depuración, junto con puntos de interrupción. Algunos lenguajes ofrecerán incluso más funcionalidades. Vea [Crear opciones de configuración del editor personalizadas y portátiles](create-portable-custom-editor-options.md) para obtener más información.  

## <a name="open-code-anywhere"></a>Apertura de código en cualquier lugar  
Puede abrir el código en Visual Studio de las maneras siguientes:  

- En la barra de menús de Visual Studio, elija **Archivo**, **Abrir**, **Carpeta** y, a continuación, busque la ubicación del código.  

- En el menú contextual (clic derecho) de una carpeta que contiene código, elija el comando **Abrir en Visual Studio**.  

- Elija el vínculo **Abrir carpeta** en la página de inicio de Visual Studio.  

- Abra el código clonado desde un repositorio de GitHub.  

### <a name="to-open-code-from-a-cloned-github-repo"></a>Para abrir el código desde un repositorio de GitHub clonado  
En el ejemplo siguiente se muestra cómo clonar un repositorio de GitHub y, a continuación, abrir su código en Visual Studio. Para seguir este procedimiento, debe tener una cuenta de GitHub y Git para Windows instalada en el sistema. Consulte [Signing up for a new GitHub account](https://help.github.com/articles/signing-up-for-a-new-github-account/) (Registro para obtener una cuenta de GitHub) y [Git for Windows](https://git-for-windows.github.io/) (Git para Windows) para obtener más información.  

1. Vaya al repositorio que quiere clonar en GitHub.  

1. Elija el botón **Clone or Download** (Clonar o descargar) y, después, elija el botón **Copiar en el Portapapeles** del menú desplegable para copiar la dirección URL segura del repositorio de GitHub.  

  ![Botón de clonar de GitHub](./media/VSIDE_Code_Clone.png)

    > [!NOTE]
    >  Aunque también tiene la opción de abrir el proyecto en el escritorio o descargar un archivo .zip del proyecto, en este ejemplo se muestra cómo clonar el repositorio mediante el método URL seguro.

1. En Visual Studio, elija la pestaña **Team Explorer** para abrir Team Explorer.  

1. En Team Explorer, en la sección **Repositorios GIT locales**, elija el comando **Clonar** y, a continuación, pegue la dirección URL de la página de GitHub en el cuadro de texto.  

  ![Clonación del proyecto](./media/VSIDE_Code_Clone2.png)

1. Elija el botón **Clonar** para clonar los archivos del proyecto en un repositorio de GIT local. Dependiendo del tamaño del repositorio, este proceso podría tardar varios minutos.  

1. Una vez que el repositorio se haya clonado en el sistema, en Team Explorer, elija el comando **Abrir** del menú contextual (clic con el botón derecho) del repositorio recién clonado.  

  ![Repositorio clonado](./media/VSIDE_Code_Clone3.png)

1. Elija el comando **Mostrar vista de carpeta** para ver los archivos en el Explorador de soluciones.  

  ![Mostrar vista de carpeta](./media/VSIDE_Code_Clone3_show.png)

  Ahora puede examinar las carpetas y los archivos del repositorio clonado y ver y buscar en el código en el editor de código de Visual Studio, con coloración de sintaxis y otras características.

    ![Búsqueda del código de proyecto clonado](./media/VSIDE_Code_Clone4.png)  

|         |         |
|---------|---------|
|  ![icono de cámara de película para vídeo](../install/media/video-icon.png "Ver un vídeo")  |    [Vea un vídeo](https://mva.microsoft.com/en-us/training-courses/getting-started-with-visual-studio-2017-17798?l=lp3TOKD6D_6711787171) sobre cómo clonar y abrir código desde un repositorio de GitHub en Visual Studio. |

## <a name="debug-your-code"></a>Depurar el código  
Puede depurar el código en Visual Studio sin un proyecto o solución. Para depurar algunos lenguajes, debe especificar un *archivo de inicio* válido en el proyecto de código, como un script, archivo ejecutable o proyecto. Visual Studio ejecuta este código especificado primero al depurar el código.  

El cuadro de lista desplegable situado junto al botón de inicio de la barra de herramientas muestra todos los elementos de inicio que Visual Studio detecta, así como los elementos que elija específicamente en una carpeta.  

![Botón Ejecutar](./media/VSIDE_Code_Run_Button.png)  

Visual Studio reconoce automáticamente los proyectos, pero es necesario que los scripts (como Python y JavaScript) se seleccionen explícitamente a fin de que aparezcan en la lista. Además, algunos elementos de inicio, como MSBuild y CMake, pueden tener varias configuraciones de compilación que aparecen en la lista desplegable del botón Ejecutar.  

Visual Studio admite actualmente la depuración para los siguientes lenguajes:  

- Node.js  

- Python  

- Proyectos de MSBuild (C#, VB, C++)  

- Cualquier archivo ejecutable con archivos PDB (depurador de Python).  

### <a name="to-debug-nodejs-and-python"></a>Para depurar Node.js y Python:  
1. Instale Node.js o Python Tools o Visual Studio 2017 y el tiempo de ejecución de Node.js.  

1. En el menú contextual de un archivo de JavaScript en el Explorador de soluciones, elija el comando **Establecer como elemento de inicio**.  

1. Elija la tecla **F5** para iniciar la depuración.  

### <a name="to-debug-msbuild-projects"></a>Para depurar proyectos de MSBuild  
1. En el menú de Visual Studio, elija **Depurar**. En el menú desplegable, elija el proyecto o seleccione el proyecto o archivo que quiere mostrar como elemento de inicio en el Explorador de soluciones.  

1. Elija la tecla **F5** para iniciar la depuración.  

### <a name="to-debug-executable-files"></a>Para depurar archivos ejecutables  
1. En el menú de Visual Studio, elija **Depurar**. En el menú desplegable, elija el proyecto o seleccione el proyecto o archivo que quiere mostrar como elemento de inicio en el Explorador de soluciones.  

1. Elija la tecla **F5** para iniciar la depuración.  

## <a name="enable-custom-build-tools"></a>Habilitación de herramientas de compilación personalizadas
Visual Studio sabe cómo ejecutar muchos lenguajes diferentes, pero no sabe cómo ejecutarlo todo. Si Visual Studio sabe cómo ejecutar su lenguaje, puede ejecutar el código de forma inmediata. Si intenta ejecutar el código pero Visual Studio no sabe cómo hacerlo, una barra de información le pedirá que designe un archivo en el código base para que actúe como elemento de inicio.  

En cambio, si el código base usa herramientas de compilación personalizadas que Visual Studio no reconoce, probablemente no podrá ejecutar ni depurar el código en Visual Studio hasta que lleve a cabo algunos pasos adicionales. Debe especificar un tipo de archivo ejecutable válido, como un compilador, junto con los argumentos y los parámetros personalizados que requiere el lenguaje. Para habilitar esta opción, Visual Studio proporciona *tareas de compilación*. Puede crear una tarea de compilación para especificar todos los elementos que un lenguaje necesita para compilar y ejecutar su código.  

También puede crear tareas de compilación arbitrarias que pueden hacer casi todo lo que desee. Por ejemplo, puede crear una tarea para mostrar el contenido de una carpeta o cambiar el nombre de un archivo. O bien, puede crear más tareas de compilación personalizadas específicas que se ocupen de tareas como compilar y generar el proyecto por medio de argumentos específicos. Los siguientes pasos muestran cómo crear ambos tipos de tareas de compilación.  

#### <a name="to-create-an-arbitrary-build-task"></a>Para crear una tarea de compilación arbitraria  
1. Elija el archivo o la carpeta del proyecto en el Explorador de soluciones donde quiere que esté la tarea y, en el menú contextual del archivo o la carpeta (clic derecho), elija **Configurar tareas**.  

  ![Configurar tareas](./media/VSIDE_Code_Config_Task.png)

  Al elegir **Configurar tareas** se abre un archivo denominado tasks.vs.json. Si este archivo no existe, se crea. Este archivo contiene las tareas de compilación para la carpeta o el archivo seleccionado.  

  ![Archivo tasks.vs.json](./media/VSIDE_Code_Tasks_JSON.png)

1. Agregue la siguiente tarea de compilación a tasks.vs.json. En este ejemplo, vamos a agregar una tarea sencilla denominada "Enumerar salidas" que muestra los archivos y subcarpetas de la carpeta seleccionada en la ventana de salida. (La nueva tarea debe agregarse dentro de la matriz de "tareas" existente).  

  ```xml
      {
        "taskName": "List outputs",
        "appliesTo": "*",
        "type": "command",
        "command": "${env.COMSPEC}",
        "args": [
          "dir ${outDir}"
        ]
      },
  ```
  La tarea de compilación completa debería tener este aspecto.  

  ![Tarea de compilación arbitraria](./media/VSIDE_Code_Tasks_ArbTask.png)

1. Guarde el proyecto.  

1. Abra el menú contextual de la carpeta seleccionada. Debería ver la nueva tarea de compilación arbitraria en la parte inferior del menú contextual.  

  ![Comando de tarea de compilación arbitraria](./media/VSIDE_Code_Tasks_ArbTask2.png)

1. Seleccione el nuevo comando **Enumerar salidas** para ejecutar la tarea.  

### <a name="to-create-a-custom-build-task"></a>Para crear una tarea de compilación personalizada
En este procedimiento, agregaremos dos tareas de compilación personalizadas que utilicen nMake para generar y limpiar el código.  

1. Elija un archivo del proyecto en el Explorador de soluciones que quiera designar más adelante como elemento de inicio. En el menú de contextual del archivo (clic derecho), elija **Configurar tareas**.  

  ![Comando de tarea de compilación personalizada](./media/VSIDE_Code_Tasks_CustTask1.png)

1. Agregue las siguientes tareas de compilación a tasks.vs.json. En este ejemplo, vamos a agregar dos tareas: una llamada "makefile-build" que usa el comando nMake para generar el proyecto, y otra llamada makefile-clean que llama al comando nMake con el argumento "clean". Estas tareas deben agregarse a la matriz de "tareas" existente. (Tenga en cuenta que estas son solo tareas de compilación de ejemplo. Para que funcionen realmente, debe tener la carga de trabajo que contiene [nNake](https://docs.microsoft.com/en-us/cpp/build/nmake-reference) instalada en el sistema).  

  ```xml
  {
  "taskName": "makefile-build",
  "appliesTo": "makefile",
  "type": "command",
  "contextType": "build",
  "command": "nmake"
  },
  {
  "taskName": "makefile-clean",
  "appliesTo": "makefile",
  "type": "command",
  "contextType": "clean",
  "command": "nmake",
  "args": [
    "clean"
    ]
  },
  ```
  La tarea de compilación personalizada completa debería tener este aspecto.  

  ![Herramienta de compilación personalizada](./media/VSIDE_Code_Tasks_CustTask2.png)

1. Guarde el proyecto.  

1. Abra el menú contextual del archivo seleccionado. Las nuevas tareas de compilación personalizadas deben aparecer en el medio del menú contextual.  

  ![Comando de tarea de compilación personalizada](./media/VSIDE_Code_Tasks_CustTask3.png)

  > [!NOTE]
  > Los comandos aparecen bajo el comando **Configurar tareas** comando debido a su configuración de `contextType`; "build" y "clean" son comandos de compilación, por lo que aparecen en la sección de compilación en el medio del menú contextual.  

  Ahora que ha asociado los comandos de compilación personalizada con el archivo, puede designar el archivo como elemento de inicio.  

1. En el menú contextual del archivo, elija **Establecer como elemento de inicio**.  

  ![Comando de tarea de compilación personalizada](./media/VSIDE_Code_Tasks_CustTask4.png)

1. En la barra de herramientas, elija la flecha desplegable situada junto al botón Inicio. El elemento de inicio aparece ahora como una opción.  

  ![Comando de tarea de compilación personalizada](./media/VSIDE_Code_Tasks_CustTask5.png)

Ahora puede elegir el botón **Inicio** o la tecla **F5** para ejecutar el código base. Puede editar y depurar el código base en Visual Studio aunque Visual Studio no reconozca las herramientas de compilación del código base. El resultado de la tarea de compilación aparece en la ventana **Salida**, y los errores de compilación aparecen en la **Lista de errores**. El archivo de la tarea de compilación de tasks.vs.json asocia el bucle de desarrollo interno de Visual Studio con las herramientas de compilación personalizadas que utiliza el código base.  

Se pueden agregar tareas de compilación personalizadas a archivos individuales o a todos los archivos de un tipo específico. Por ejemplo, los archivos de paquete de NuGet pueden configurarse para que tengan una tarea "Restaurar paquetes", o todos los archivos de origen pueden configurarse para que tengan una tarea de análisis estático, como un linter para todos los archivos .js.  

Visual Studio admite la sustitución de `$variable` de VSCode en la raíz de tasks.vs.json, además de las claves o variables de entorno (como `$env.var`).  

## <a name="specify-build-output"></a>Especificación de la salida de la compilación  
Si se debe compilar el proyecto, puede agregar una etiqueta adicional denominada `output` al archivo tasks.vs.json. A continuación se muestra un ejemplo.  

`"output": "${workspaceRoot}\\bin\\hellomake.exe"`

Al especificar la ubicación de salida se notifica a Visual Studio dónde encontrar la salida de la compilación del proyecto.  

## <a name="tasksvsjson-file-location"></a>Ubicación del archivo tasks.vs.json  
De forma predeterminada, el archivo tasks.vs.json se encuentra en una carpeta oculta denominada `.vs`. Para ver los archivos ocultos en Visual Studio, elija el botón **Mostrar todos los archivos** en la barra de herramientas del Explorador de soluciones.  

![Comando de tarea de compilación arbitraria](./media/VSIDE_Code_Tasks_FileLocation.png)

El archivo tasks.vs.json está oculto porque la mayoría de los usuarios normalmente no desea insertarlo en el repositorio del control de código fuente. Sin embargo, si desea poder insertarlo en el repositorio del control de código fuente, arrastre el archivo a la raíz del proyecto donde estará visible.  

Otros archivos .json pueden encontrarse en la carpeta .vs, pero los únicos que se deben mover son el archivo tasks.vs.json y el archivo launch.vs.json (si está presente). El archivo launch.vs.json configura el depurador de Visual Studio, mientras que el archivo tasks.vs.json configura la compilación en Visual Studio.  

## <a name="see-also"></a>Vea también
[Escribir código en el editor de código y texto](../ide/writing-code-in-the-code-and-text-editor.md)
