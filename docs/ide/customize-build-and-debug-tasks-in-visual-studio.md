---
title: "Personalización de las tareas de compilación y depuración en Visual Studio mediante tasks.vs.json y launch.vs.json | Microsoft Docs"
ms.date: 02/21/2018
ms.technology: vs-ide-general
ms.topic: article
helpviewer_keywords:
- NMAKE [Visual Studio]
- makefiles [Visual Studio]
- customize codebases [Visual Studio]
- tasks.vs.json file [Visual Studio]
- launch.vs.json file [Visual Studio]
- vsworkspacesettings.json file [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5d40bd35d893afeb8e76e18d46185b3d63add1c5
ms.sourcegitcommit: 3abca1c733af876c8146daa43a62e829833be280
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="customize-build-and-debug-tasks-for-open-folder-development"></a>Personalización de las tareas de compilación y depuración para el desarrollo de "Abrir carpeta"

Visual Studio sabe cómo ejecutar varios lenguajes y bases de datos diferentes, pero no sabe cómo ejecutarlo todo. Si [abrió una carpeta de código](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) en Visual Studio y Visual Studio sabe cómo ejecutar el código, puede ejecutarlo de inmediato sin ninguna configuración adicional.

Si el código base usa herramientas de compilación personalizadas que Visual Studio no reconoce, debe proporcionar algunos detalles de configuración para ejecutar y depurar el código en Visual Studio. Mediante la definición de *tareas de compilación*, le indica a Visual Studio cómo compilar el código. Puede crear una o varias tareas de compilación para especificar todos los elementos que un lenguaje necesita para compilar y ejecutar su código. También puede crear tareas arbitrarias que pueden hacer casi todo lo que desee. Por ejemplo, puede crear una tarea para mostrar el contenido de una carpeta o cambiar el nombre de un archivo.

Use estos archivos *.json* para personalizar el código base sin proyecto:

|Nombre del archivo|Propósito|
|-|-|
|*tasks.vs.json*|Especifique los modificadores del compilador y los comandos de compilación personalizada, además de las tareas arbitrarias (no relacionadas con la compilación).<br>Se accede a través del elemento del menú contextual del **Explorador de soluciones** **Configurar tareas**.|
|*launch.vs.json*|Especifique los argumentos de la línea de comandos para realizar la depuración.<br>Se accede a través del elemento del menú contextual del **Explorador de soluciones** **Configuración de depuración e inicio**.|
|*VSWorkspaceSettings.json*|Configuración genérica que podría afectar las tareas y el inicio. Por ejemplo, definir `envVars` en *VSWorkspaceSettings.json* agrega las variables de entorno especificadas para ejecutar los comandos de manera externa.<br>Puede crear manualmente este archivo.|

Estos archivos *.json* se encuentran en una carpeta oculta llamada *.vs* en la carpeta raíz del código base. Visual Studio crea los archivos *tasks.vs.json* y *launch.vs.json* según sea necesario cuando se elija **Configurar tareas** o **Configuración de depuración e inicio** en un archivo o una carpeta del **Explorador de soluciones**. Estos archivos *.json* están ocultos porque los usuarios habitualmente no desean insertarlos en el control de código fuente. Sin embargo, si desea poder insertarlos en el control de código fuente, arrastre los archivos a la raíz del código base, donde estarán visibles.

> [!TIP]
> Para ver los archivos ocultos en Visual Studio, elija el botón **Mostrar todos los archivos** en la barra de herramientas del Explorador de soluciones.

## <a name="define-tasks-with-tasksvsjson"></a>Definición de tareas con tasks.vs.json

Puede automatizar los scripts de compilación o cualquier otra operación externa en los archivos que tiene en el área de trabajo actual al ejecutarlos directamente en el IDE. Para configurar una tarea nueva, haga clic con el botón derecho en un archivo o una carpeta y seleccione **Configurar tareas**.

![Menú Configurar tareas](../ide/media/customize-configure-tasks-menu.png)

De este modo, se crea (o abre) el archivo *tasks.vs.json* en la carpeta *.vs*. En este archivo, puede definir una tarea de compilación o una tarea arbitraria y luego invocarla con el nombre que le asignó desde el menú contextual del **Explorador de soluciones**.

Se pueden agregar tareas personalizadas a archivos individuales o a todos los archivos de un tipo específico. Por ejemplo, los archivos de paquete de NuGet pueden configurarse para que tengan una tarea "Restaurar paquetes" o todos los archivos de origen pueden configurarse para que tengan una tarea de análisis estático, como un linter para todos los archivos *.js*.

### <a name="define-custom-build-tasks"></a>Definición de las tareas de compilación personalizadas

Si el código base usa las herramientas de compilación personalizadas que Visual Studio no reconoce, no podrá ejecutar ni depurar el código en Visual Studio hasta que complete algunos pasos de configuración. Visual Studio proporciona *tareas de compilación* en las que puede indicar a Visual Studio cómo compilar, recompilar y limpiar el código. El archivo de tarea de compilación *tasks.vs.json* asocia el bucle de desarrollo interno de Visual Studio con las herramientas de compilación personalizadas que usa el código base.

Considere un código base que consta de un solo archivo de C# llamado *hello.cs*. El archivo Make para este tipo de código base podría tener el aspecto siguiente:

```makefile
build: directory hello.exe

hello.exe: hello.cs
    csc -debug hello.cs /out:bin\hello.exe

clean:
    del bin\hello.exe bin\hello.pdb

rebuild: clean build

directory: bin

bin:
    md bin
```

Para este tipo de archivo Make que contiene objetivos de compilación, limpieza y recompilación, es posible definir el archivo *tasks.vs.json* siguiente. Contiene tres tareas de compilación para compilar, recompilar y limpiar el código base, con NMAKE como la herramienta de compilación.

```json
{
  "version": "0.2.1",
  "outDir": "\"${workspaceRoot}\\bin\"",
  "tasks": [
    {
      "taskName": "makefile-build",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "build",
      "command": "nmake",
      "args": [ "build" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    },
    {
      "taskName": "makefile-clean",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "clean",
      "command": "nmake",
      "args": [ "clean" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    },
    {
      "taskName": "makefile-rebuild",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "rebuild",
      "command": "nmake",
      "args": [ "rebuild" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    }
  ]
}
```

Una vez que se definen las tareas de compilación en *tasks.vs.json*, se agregan elementos de menú contextual adicionales a los archivos correspondientes en el **Explorador de soluciones**. En este ejemplo, las opciones **Build** (Compilar), **Rebuild** (Recompilar) y **Clean** (Limpiar) se agregan al menú contextual de cualquier *archivo MAKE*.

![menú contextual de archivo MAKE con opción de compilar, recompilar y limpiar](media/customize-build-rebuild-clean.png)

> [!NOTE]
> Los comandos aparecen en el menú contextual bajo el comando **Configurar tareas** debido a la configuración de `contextType`. "build", "rebuild" y "clean" son comandos de compilación, por lo que aparecen en la sección de compilación al medio del menú contextual.

Cuando selecciona una de estas opciones, se ejecuta la tarea. El resultado aparece en la ventana **Salida** y los errores de compilación, en la **Lista de errores**.

### <a name="define-arbitrary-tasks"></a>Definición de las tareas arbitrarias

Puede definir tareas arbitrarias en el archivo *tasks.vs.json* para hacer prácticamente lo que desee. Por ejemplo, puede definir una tarea para mostrar el nombre del archivo actualmente seleccionado en la ventana **Salida** o para mostrar los archivos de un directorio específico.

En el ejemplo siguiente se muestra un archivo *tasks.vs.json* que define una sola tarea. Cuando se invoca, la tarea muestra el nombre del archivo *.js* actualmente seleccionado.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskName": "Echo filename",
      "appliesTo": "*.js",
      "type": "default",
      "command": "${env.COMSPEC}",
      "args": [ "echo ${file}" ]
    }
  ]
}
```

- `taskName` especifica el nombre que aparece en el menú contextual.
- `appliesTo` especifica los archivos en los que se puede realizar el comando.
- La propiedad `command` especifica el comando que se va a invocar. En este ejemplo, la variable de entorno `COMSPEC` se usa para identificar el intérprete de la línea de comandos, habitualmente *cmd.exe*.
- La propiedad `args` especifica los argumentos que se pasarán al comando invocado.
- La macro `${file}` recupera el archivo seleccionado en el **Explorador de soluciones**.

Después de guardar *tasks.vs.json*, puede hacer clic con el botón derecho en algún archivo *.js* de la carpeta y elegir **Echo filename** (Nombre de archivo de echo). El nombre de archivo se muestra en la ventana **Salida**.

> [!NOTE]
> Si el código base no contiene un archivo *tasks.vs.json*, puede crear uno si elige **Configurar tareas** con el botón derecho o en el menú contextual de un archivo en el **Explorador de soluciones**.

En el ejemplo siguiente se define una tarea que muestra los archivos y las subcarpetas del directorio *bin*.

```json
{
  "version": "0.2.1",
  "outDir": "\"${workspaceRoot}\\bin\"",
  "tasks": [
    {
      "taskName": "List Outputs",
      "appliesTo": "*",
      "type": "default",
      "command": "${env.COMSPEC}",
      "args": [ "dir ${outDir}" ]
    }
  ]
}
```

- `${outDir}` es una macro personalizada que se define en primer lugar, antes del bloque `tasks`. Luego se llama en la propiedad `args`.

Esta tarea se aplica a todos los archivos. Cuando abre el menú contextual de algún archivo en el **Explorador de soluciones**, **Enumerar salidas** del nombre de la tarea aparece en la parte inferior del menú. Cuando elige **Enumerar salidas**, el contenido del directorio *bin* aparece en la ventana **Salida** de Visual Studio.

![Tarea arbitraria en el menú contextual](../ide/media/customize-arbitrary-task-menu.png)

### <a name="settings-scope"></a>Ámbito de configuración

Puede haber varios archivos *tasks.vs.json* en la raíz y en los subdirectorios de un código base. Este diseño permite la flexibilidad necesaria para tener distintos comportamientos en diferentes subdirectorios del código base. Visual Studio agrega o invalida la configuración en todo el código base y establece la prioridad de los archivos en el siguiente orden:

- Los archivos de configuración del directorio *.vs* de la carpeta raíz.
- El directorio donde se procesa una configuración.
- El directorio principal del directorio actual, hasta llegar al directorio raíz.
- Los archivos de configuración del directorio raíz.

Estas reglas de agregación se aplican a los archivos *tasks.vs.json* y *VSWorkspaceSettings.json*. Para información sobre cómo se agrega configuración en otro archivo, consulte la sección correspondiente a dicho archivo en este artículo.

### <a name="properties-for-tasksvsjson"></a>Propiedades de tasks.vs.json

En esta sección se describe parte de las propiedades que puede especificar en *tasks.vs.json*.

#### <a name="appliesto"></a>appliesTo

Puede crear tareas para cualquier archivo o carpeta si especifica su nombre en el campo `appliesTo`, por ejemplo `"appliesTo": "hello.js"`. Las máscaras de archivo siguientes se pueden usar como valores:

|||
|-|-|
|`"*"`| tarea disponible para todos los archivos y carpetas del área de trabajo|
|`"*/"`| tarea disponible para todas las carpetas del área de trabajo|
|`"*.js"`| tarea disponible para todos los archivos con extensión .js del área de trabajo|
|`"/*.js"`| tarea disponible para todos los archivos con extensión .js en la raíz del área de trabajo|
|`"src/*/"`| tarea disponible para todas las subcarpetas de la carpeta "src"|
|`"makefile"`| tarea disponible para todos los archivos Make del área de trabajo|
|`"/makefile"`| tarea disponible solo para el archivo Make que se encuentra en la raíz del área de trabajo|

#### <a name="macros-for-tasksvsjson"></a>Macros de tasks.vs.json

|||
|-|-|
|`${env.<VARIABLE>}`| Especifica cualquier variable de entorno (por ejemplo, ${env.PATH}, ${env.COMSPEC}, etc.) que esté establecida para el símbolo del sistema para desarrolladores. Para más información, consulte [Símbolo del sistema para desarrolladores de Visual Studio](/dotnet/framework/tools/developer-command-prompt-for-vs).|
|`${workspaceRoot}`| La ruta de acceso completa a la carpeta del área de trabajo (por ejemplo, "C:\sources\hello")|
|`${file}`| La ruta de acceso completa del archivo o la carpeta en que se selecciona la ejecución de esta tarea (por ejemplo, "C:\sources\hello\src\hello.js")|
|`${relativeFile}`| La ruta de acceso relativa al archivo o la carpeta (por ejemplo, "src\hello.js")|
|`${fileBasename}`| El nombre del archivo sin ruta de acceso ni extensión (por ejemplo, "hello")|
|`${fileDirname}`| La ruta de acceso completa al archivo, sin el nombre de archivo (por ejemplo, "C:\sources\hello\src")|
|`${fileExtname}`| La extensión del archivo seleccionado (por ejemplo, ".js")|

## <a name="configure-debugging-with-launchvsjson"></a>Configuración de la depuración con launch.vs.json

1. Para configurar el código base para realizar la depuración, en el **Explorador de soluciones**, elija el elemento de menú **Configuración de depuración e inicio** con un clic con el botón derecho o con el menú contextual del archivo ejecutable.

   ![Menú contextual Configuración de depuración e inicio](media/customize-debug-launch-menu.png)

1. En el cuadro de diálogo **Seleccionar un depurador**, elija una opción y, luego, elija el botón **Seleccionar**.

   ![Cuadro de diálogo Seleccionar un depurador](media/customize-select-a-debugger.png)

   Si el archivo *launch.vs.json* todavía no existe, se creará.

   ```json
   {
     "version": "0.2.1",
     "defaults": {},
     "configurations": [
       {
         "type": "default",
         "project": "bin\\hello.exe",
         "name": "hello.exe"
       }
     ]
   }
   ```

1. A continuación, haga clic con el botón derecho en el archivo ejecutable en el **Explorador de soluciones**y elija **Establecer como elemento de inicio**.

   El archivo ejecutable se designa como el elemento de inicio del código base y el título del botón **Iniciar** de la depuración cambia para reflejar el nombre del archivo ejecutable.

   ![Botón Iniciar personalizado](media/customize-start-button.png)

   Cuando presiona **F5**, el depurador se inicia y se detiene en cualquier punto de interrupción que se pueda haber establecido. Todas las ventanas familiares del depurador están disponibles y en funcionamiento.

### <a name="specify-arguments-for-debugging"></a>Especificación de argumentos para la depuración

Puede especificar los argumentos de la línea de comandos que se van a pasar para realizar la depuración en el archivo *launch.vs.json*. Agregue los argumentos de la matriz `args`, tal como se muestra en el ejemplo siguiente:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "bin\\hello.exe",
      "name": "hello.exe"
    },
    {
      "type": "default",
      "project": "bin\\hello.exe",
      "name": "hello.exe a1",
      "args": [ "a1" ]
    }
  ]
}
```

Cuando guarda este archivo, el nombre de la configuración nueva aparece en la lista desplegable de destinos de depuración y puede seleccionarlo para iniciar el depurador. Puede crear tantas configuraciones de depuración como desee.

![Lista desplegable de configuraciones de depuración](media/customize-debug-configurations.png)

> [!NOTE]
> La propiedad de la matriz `configurations` en *launch.vs.json* se lee desde dos ubicaciones&mdash;el directorio raíz del código base y el directorio *.vs*. Si se produce algún conflicto, la prioridad la tiene el valor que aparece en *.vs\launch.vs.json*.

## <a name="define-workspace-settings-in-vsworkspacesettingsjson"></a>Definición de la configuración del área de trabajo en VSWorkspaceSettings.json

Puede especificar la configuración genérica que puede afectar las tareas e iniciarse en el archivo *VSWorkspaceSettings.json*. Por ejemplo, si define `envVars` en *VSWorkspaceSettings.json*, Visual Studio agrega las variables de entorno especificadas a los comandos que se ejecutan de manera externa. Para usar este archivo, debe crearlo de manera manual.

## <a name="additional-settings-files"></a>Archivos de configuración adicionales

Además de los tres archivos *.json* que se describen en este tema, Visual Studio también lee la configuración de algunos archivos adicionales, si existen en el código base.

### <a name="vscodesettingsjson"></a>.vscode\settings.json

Visual Studio lee la configuración limitada de un archivo denominado *settings.json*, si se encuentra en un directorio llamado *.vscode*. Esta funcionalidad se proporciona para los códigos base que se desarrollaron anteriormente en Visual Studio Code. Actualmente, la única configuración que se lee de *.vscode\settings.json* es `files.exclude`, que filtra los archivos de manera visual en el Explorador de soluciones y desde algunas herramientas de búsqueda.

Puede tener cualquier número de archivos *.vscode\settings.json* en el código base. La configuración que se lee de este archivo se aplica al directorio principal de *.vscode* y a todos los subdirectorios.

### <a name="gitignore"></a>.gitignore

Los archivos *.gitignore* se usan para indicar a Git los archivos que debe omitir; es decir, cuáles son los archivos y directorios que no desea insertar en el repositorio. Los archivos *.gitignore* se incluyen habitualmente como parte de un código base para que la configuración se pueda compartir con todos los desarrolladores del código base. Visual Studio lee patrones en los archivos *.gitignore* para filtrar los archivos de manera visual y desde algunas herramientas de búsqueda.

La configuración que se lee del archivo *.gitignore* se aplica al directorio principal y a todos los subdirectorios.

## <a name="see-also"></a>Vea también

- [Desarrollo de código en Visual Studio sin proyectos o soluciones](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Open Folder projects for C++](/cpp/ide/non-msbuild-projects) (Proyectos Abrir carpeta para C++)
- [CMake projects in C++](/cpp/ide/cmake-tools-for-visual-cpp) (Proyectos CMake en C++)
- [Referencia de NMAKE](/cpp/build/nmake-reference)
- [Escribir código en el editor de código y texto](../ide/writing-code-in-the-code-and-text-editor.md)