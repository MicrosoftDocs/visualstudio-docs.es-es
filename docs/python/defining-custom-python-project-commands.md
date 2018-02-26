---
title: "Cómo definir comandos de menú personalizados para proyectos de Python en Visual Studio | Microsoft Docs"
description: "Se explica cómo modificar los archivos de proyecto y de destinos para agregar comandos personalizados al menú contextual del proyecto de Python en Visual Studio. Los comandos se pueden invocar en programas ejecutables, en scripts, en módulos, en fragmentos de código en línea y en pip."
ms.custom: 
ms.date: 02/02/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 1fa4c68b1d7dc89452376d6efc47e047f75d52d6
ms.sourcegitcommit: 06cdc1651aa7f45e03d260080da5a623d6258661
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2018
---
# <a name="defining-custom-commands-for-python-projects"></a>Definición de comandos personalizados para proyectos de Python

Al trabajar con proyectos de Python, posiblemente le haya ocurrido que ha cambiado a una ventana de comandos para ejecutar módulos o scripts específicos, ejecutar comandos de pip o ejecutar alguna otra herramienta al azar. Para mejorar este flujo de trabajo, se pueden agregar comandos personalizados al submenú **Python** en el menú contextual del proyecto de Python. Esos comandos se pueden ejecutar en una ventana de consola o en la ventana de salida de Visual Studio. También se pueden usar expresiones regulares para indicar a Visual Studio cómo analizar los errores y advertencias de la salida del comando.

Este menú contiene de forma predeterminada un solo comando, **Ejecutar PyLint**:

![Apariencia predeterminada del submenú Python en el menú contextual de un proyecto](media/custom-commands-default-menu.png)

Los comandos personalizados aparecen en este mismo menú contextual. Los comandos personalizados se agregan a un archivo de proyecto directamente cuando son de aplicación en ese proyecto individual en cuestión. Los comandos personalizados también se pueden definir en un archivo `.targets` que se puede importar fácilmente a varios archivos de proyecto.

Algunas plantillas de proyecto de Python en Visual Studio ya agregan sus propios comandos personalizados por medio de su archivo `.targets`. Por ejemplo, las plantillas Proyecto web de Bottle y Proyecto web de Flask agregan dos comandos, **Iniciar servidor** e **Iniciar el servidor de depuración**. La plantilla Proyecto web de Django agrega esos mismos comandos y unos cuantos más:

![Apariencia del submenú Python en el menú contextual de un proyecto de Django](media/custom-commands-django-menu.png)

Cada comando personalizado puede hacer referencia a un archivo de Python, a un módulo de Python, a código de Python en línea, a un archivo ejecutable al azar o a un comando de pip. También puede especificar cómo y dónde se ejecuta el comando.

> [!Tip]
> Cada vez que se realicen cambios en un archivo de proyecto en un editor de texto, será necesario volver a cargar el proyecto en Visual Studio para que esos cambios surtan efecto. Por ejemplo, deberá volver a cargar un proyecto después de agregar definiciones de comando personalizado para que esos comandos aparezcan en el menú contextual de dicho proyecto.
>
> Como ya sabrá, Visual Studio permite editar el archivo de proyecto directamente. En primer lugar, haga clic con el botón derecho en el archivo de proyecto y seleccione **Descargar el proyecto**; luego, haga clic con el botón derecho de nuevo y seleccione **Editar (nombre del proyecto)** para abrir el proyecto en el editor de Visual Studio. Hacemos y guardamos las modificaciones necesarias, hacemos clic con el botón derecho en el proyecto una vez más y seleccionamos **Volver a cargar el proyecto**, que le pedirá confirmación para cerrar el archivo de proyecto en el editor.
>
> Bien es cierto que todos estos clics pueden resultar tediosos al desarrollar un comando personalizado. Para lograr un flujo de trabajo más eficaz, cargue el proyecto en Visual Studio y abra el archivo `'.pyproj` también en un editor aparte (por ejemplo, en otra instancia de Visual Studio, en Visual Studio Code, en el Bloc de notas, etc.). Al guardar los cambios en el editor y cambiar a Visual Studio, Visual Studio detecta los cambios y le pregunta si desea volver a cargar el proyecto ("El proyecto [nombre] se ha modificado fuera del entorno"). Seleccione **Volver a cargar**. Los cambios se aplicarán inmediatamente en un solo paso.

## <a name="walkthrough-add-a-command-to-a-project-file"></a>Tutorial: Agregar un comando a un archivo de proyecto

Para familiarizarse con los comandos personalizados, en esta sección se describe un ejemplo sencillo en el que se ejecuta el archivo de inicio de un proyecto directamente con python.exe (un comando de ese tipo es, a todos los efectos, lo mismo que usar **Depurar > Iniciar sin depurar**).

1. Cree un proyecto denominado "Python-CustomCommands" con la plantilla "Aplicación de Python" (vea [Inicio rápido: Crear un proyecto de Python desde una plantilla en Visual Studio](quickstart-02-project-from-template.md) para obtener instrucciones si aún no está familiarizado con el proceso).

1. En `Python_CustomCommands.py`, agregue el código `print("Hello custom commands")`.

1. Haga clic con el botón derecho en el proyecto en el **Explorador de soluciones**, seleccione **Python** y fíjese en que el único comando que aparece en el submenú es **Ejecutar PyLint**. Los comandos personalizados aparecen en este mismo submenú.

1. Tal y como se sugiere en la introducción, abra `Python-CustomCommands.pyproj` en un editor de texto aparte. Después, agregue las siguientes líneas al final del archivo, justo dentro del elemento `</Project>` de cierre, y guarde el archivo.

    ```xml
    <PropertyGroup>
      <PythonCommands>
        $(PythonCommands);
      </PythonCommands>
    </PropertyGroup>
    ```

1. Cambie a Visual Studio y seleccione **Volver a cargar** cuando le pregunte acerca del cambio de archivo. Tras ello, consulte de nuevo el menú **Python** para ver que **Ejecutar PyLint** sigue siendo el único elemento aparece, dado que las líneas que hemos agregado replican únicamente el grupo de propiedades `<PythonCommands>` predeterminado que contiene el comando de PyLint.

1. Cambie al editor con el archivo de proyecto y agregue la siguiente definición de `<Target>` después de `<PropertyGroup>`. Como se explica más adelante en este artículo, este elemento `Target` define un comando personalizado para ejecutar el archivo de inicio (identificado por la propiedad "StartupFile") por medio de `python.exe` en una ventana de la consola. El atributo `ExecuteIn="consolepause"` usa una consola que espera a que el usuario presione una tecla antes de cerrarse.

    ```xml
    <Target Name="Example_RunStartupFile" Label="Run startup file" Returns="@(Commands)">
      <CreatePythonCommandItem
        TargetType="script"
        Target="$(StartupFile)"
        Arguments=""
        WorkingDirectory="$(MSBuildProjectDirectory)"
        ExecuteIn="consolepause">
        <Output TaskParameter="Command" ItemName="Commands" />
      </CreatePythonCommandItem>
    </Target>
    ```

1. Agregue el valor del atributo `Name` del destino al grupo de propiedades `<PythonCommands>` que agregamos anteriormente para que el elemento sea similar al siguiente código. El nombre del destino que agregamos a esta lista es lo que se incorpora al menú de **Python**.

    ```xml
      <PythonCommands>
        $(PythonCommands);
        Example_RunStartupFile
      </PythonCommands>
    ```

    Si quiere que el comando aparezca antes que los que hay definidos en `$(PythonCommands)`, colóquelo antes de ese token.

1. Guarde el archivo de proyecto, cambie a Visual Studio y vuelva a cargar el proyecto cuando se le pida. Después, haga clic con el botón derecho en el proyecto "Python CustomCommands" y seleccione **Python**. Debería haber un elemento **Run startup file** (Ejecutar archivo de inicio) en el menú. Si no lo ve, confirme que ha agregado el nombre al elemento `<PythonCommands>`. Vea también [Solución de problemas](#troubleshooting) más adelante en este artículo.

    ![Comando personalizado en el submenú contextual de Python](media/custom-commands-walkthrough-menu-item.png)

1. Seleccione el comando **Run startup file**; deberá abrirse una ventana de comandos con el texto "Hello custom commands" seguido de "Presione cualquier tecla para continuar. . .".  Presione cualquier tecla para cerrar la ventana.

    ![Resultado del comando personalizado en una ventana de la consola](media/custom-commands-walkthrough-console.png)

1. Vuelva al editor con el archivo de proyecto abierto y cambie el valor del atributo `ExecuteIn` a `output`. Guarde el archivo, cambie a Visual Studio, vuelva a cargar el proyecto e invoque el comando de nuevo. Esta vez, verá que la salida del programa se muestra en la ventana **Resultados** de Visual Studio:

    ![Resultado del comando personalizado en la ventana de salida](media/custom-commands-walkthrough-output-window.png)

1. Para agregar más comandos, defina un elemento `<Target>` adecuado para cada comando, agregue el nombre del destino al grupo de propiedades `<PythonCommands>` y vuelva a cargar el proyecto en Visual Studio.

>[!Tip]
> Si invoca un comando que usa propiedades del proyecto, como `($StartupFile)`, y se produce un error en ese comando porque no hay un token definido, Visual Studio lo deshabilita hasta que el proyecto se vuelva a cargar. Realizar cambios en el proyecto que definan la propiedad no hace que el estado de estos comandos se actualice, de modo que en esos casos seguirá siendo necesario volver a cargar el proyecto.

## <a name="command-target-structure"></a>Estructura de destino de comando

En el siguiente pseudocódigo se muestra la forma general del elemento `<Target>`:

```xml
<Target Name="Name1" Label="Display Name" Returns="@(Commands)">
    <CreatePythonCommandItem Target="filename, module name, or code"
        TargetType="executable/script/module/code/pip"
        Arguments="..."
        ExecuteIn="console/consolepause/output/repl[:Display name]/none"
        WorkingDirectory="..."
        ErrorRegex="..."
        WarningRegex="..."
        RequiredPackages="...;..."
        Environment="...">

      <!-- Output always appears in this form, with these exact attributes -->
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

Para hacer referencia a propiedades del proyecto o a variables de entorno en los valores de atributo, use el nombre dentro de un token `$()`, como `$(StartupFile)` y `$(MSBuildProjectDirectory)`. Para más información, vea [Propiedades de MSBuild](../msbuild/msbuild-properties.md).

### <a name="target-attributes"></a>Atributos de destino

| Atributo | Obligatorio | Description |
| --- | --- | --- |
| nombre | Sí | Identificador del comando dentro del proyecto de Visual Studio. Este nombre debe estar incluido en el grupo de propiedades `<PythonCommands>` para que el comando aparezca en el submenú Python. |
| Etiqueta | Sí | Nombre para mostrar de interfaz de usuario que aparece en el submenú Python. |
| Valores devueltos | Sí | Debe contener `@(Commands)`, que identifica el destino como un comando. |

### <a name="createpythoncommanditem-attributes"></a>Atributos CreatePythonCommandItem

Ninguno de los valores de atributo distingue entre mayúsculas y minúsculas.

| Atributo | Obligatorio | Description |
| --- | --- | --- |
| TargetType | Sí | Especifica lo que el atributo Target contiene y cómo se usa junto con el atributo Arguments:<ul><li>**executable**: Se ejecuta el archivo ejecutable mencionado en Target, lo que anexa el valor en Arguments, como si se insertara directamente en la línea de comandos. El valor debe contener solo un nombre de programa, sin argumentos.</li><li>**script**: Se ejecuta `python.exe` con el nombre de archivo mencionado en Target, seguido del valor reflejado en Arguments.</li><li>**module**: Se ejecuta `python -m` seguido del nombre de módulo mencionado en Target y seguido del valor en Arguments.</li><li>**code**: Se ejecuta el código en línea incluido en Target. El valor de Arguments se omite.</li><li>**pip**: Se ejecuta `pip` con el comando mencionado en Target seguido de Arguments; pero si ExecuteIn está establecido en "output", pip da por hecho el comando `install` y usa Target como el nombre de paquete.</li></ul> |
| Destino | Sí | Nombre de archivo, nombre de módulo, código o comando pip que se usa en función de TargetType. |
| Argumentos | Optional | Especifica una cadena de argumentos (si los hay) que proporcionar al destino. Cabe decir que cuando TargetType es `script`, los argumentos se proporcionan al programa de Python, no a `python.exe`. Este elemento se omite en el TargetType `code`. |
| ExecuteIn | Sí | Especifica el entorno en el que se va a ejecutar el comando:<ul><li>**console**: (Valor predeterminado) Se ejecuta Target y los argumentos correspondientes como si se hubieran escrito directamente en la línea de comandos. Mientras Target se está ejecutando, se abre una ventana de comandos, que al finalizar se cierra automáticamente.</li><li>**consolepause**: El proceso es el mismo que con console, pero se espera a que el usuario presione una tecla para cerrar la ventana.</li><li>**output**: Se ejecuta Target y se muestran los resultados en la ventana Resultados de Visual Studio. Si TargetType es "pip", Visual Studio usa Target como el nombre del paquete y anexa los argumentos indicados en Arguments.</li><li>**repl**: Se ejecuta Target en la [ventana interactiva de Python](interactive-repl.md); el nombre para mostrar opcional se usa como título de la ventana.</li><li>**none**: El comportamiento es el mismo que con console.</li></ul>|
| WorkingDirectory | Optional | Carpeta en la que se va a ejecutar el comando. |
| ErrorRegex<br>WarningRegEx | Optional | Se usa únicamente cuando ExecuteIn es `output`. Ambos valores especifican una expresión regular con la que Visual Studio analiza los resultados del comando para mostrar los errores y las advertencias en la ventana Lista de errores. Si no se especifica, el comando no afecta a la ventana Lista de errores. Para más información sobre qué espera Visual Studio, vea [Grupos de capturas con nombre](#named-capture-groups-for-regular-expression). |
| RequiredPackages | Optional | Lista de requisitos de paquete del comando en el que se usa el mismo formato que en [requirements.txt](https://pip.readthedocs.io/en/1.1/requirements.html) (pip.readthedocs.io). El comando **Ejecutar PyLint**, por ejemplo, especifica `pylint>=1.0.0`. Antes de ejecutar el comando, Visual Studio comprueba que todos los paquetes que figuran en la lista están instalados. Visual Studio usa pip para instalar los paquetes que faltan. |
| Entorno | Optional | Cadena de variables de entorno que hay que definir antes de ejecutar el comando. Cada variable usa el formato NAME=VALUE con varias variables separadas por punto y coma. Una variable con varios valores debe incluirlos entre comillas simples o dobles, por ejemplo, "NAME=VALUE1;VALUE2". |

#### <a name="named-capture-groups-for-regular-expressions"></a>Grupos de capturas con nombre de expresiones regulares

Al analizar los errores y advertencias de la salida de un comando, Visual Studio espera que las expresiones regulares en los valores `ErrorRegex` y `WarningRegex` usen los siguientes grupos con nombre:

- `(?<message>...)`: Texto del error.
- `(?<code>...)`: Código del error.
- `(?<filename>...)`: Nombre del archivo sobre el que versa el error.
- `(?<line>...)`: Número de línea de la ubicación en el archivo sobre el que versa el error.
- `(?<column>...)`: Número de columna de la ubicación en el archivo sobre el que versa el error.

Por ejemplo, PyLint muestra advertencias de la siguiente forma:

```output
************* Module hello
C:  1, 0: Missing module docstring (missing-docstring)
```

Para permitir que Visual Studio extraiga la información correcta de esas advertencias y las muestre en la ventana **Lista de errores**, el valor de `WarningRegex` en el comando **Ejecutar Pylint** es el siguiente:

```regex
^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]
```

Tenga en cuenta que `msg_id` en el valor debe ser en realidad `code`; vea el [problema 3680](https://github.com/Microsoft/PTVS/issues/3680).

## <a name="creating-a-targets-file-with-custom-commands"></a>Crear un archivo .targets con comandos personalizados

Cuando se definen comandos personalizados en un archivo de proyecto, estarán disponibles única y exclusivamente para ese archivo de proyecto. Para usar comandos en varios archivos de proyecto, hay que definir en su lugar el grupo de propiedades `<PythonCommands>` y todos sus elementos `<Target>` en un archivo `.targets` y, luego, importar ese archivo a los archivos de proyecto individuales que se quiera.

El archivo `.targets` tiene el siguiente formato:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PythonCommands>
      $(PythonCommands);
      <!-- Additional command names -->
    </PythonCommands>
  </PropertyGroup>

  <Target Name="..." Label="..." Returns="@(Commands)">
    <!-- CreatePythonCommandItem and Output elements... -->
  </Target>

  <!-- Any number of additional Target elements-->
</Project>
```

Para cargar un archivo `.targets` en un proyecto, coloque un elemento `<Import Project="(path)">` en cualquier lugar dentro del elemento `<Project>`. Por ejemplo, si tiene un archivo llamado `CustomCommands.targets` en una subcarpeta `targets` en el proyecto, use el siguiente código:

```xml
<Import Project="targets/CustomCommands.targets"/>
```

> [!Note]
> Cada vez que el archivo `.targets` cambie, será necesario volver a cargar la *solución* que contiene el proyecto, no solo el proyecto en sí.

## <a name="example-commands"></a>Comandos de ejemplo

### <a name="run-pylint-module-target"></a>Ejecutar PyLint (Target: module)

El siguiente código aparece en el archivo `Microsoft.PythonTools.targets`:

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);PythonRunPyLintCommand</PythonCommands>
  <PyLintWarningRegex>
    <![CDATA[^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]>
  </PyLintWarningRegex>
</PropertyGroup>

<Target Name="PythonRunPyLintCommand"
        Label="resource:Microsoft.PythonTools.Common;Microsoft.PythonTools.Common.Strings;RunPyLintLabel"
        Returns="@(Commands)">
  <CreatePythonCommandItem Target="pylint.lint"
                           TargetType="module"
                           Arguments="&quot;--msg-template={abspath}({line},{column}): warning {msg_id}: {msg} [{C}:{symbol}]&quot; -r n @(Compile, ' ')"
                           WorkingDirectory="$(MSBuildProjectDirectory)"
                           ExecuteIn="output"
                           RequiredPackages="pylint&gt;=1.0.0"
                           WarningRegex="$(PyLintWarningRegex)">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-pip-install-with-a-specific-package-pip-target"></a>Ejecutar pip install con un paquete específico (Target: pip)

El siguiente comando ejecuta `pip install my-package` en la ventana de salida. Puede usar un comando de este tipo al desarrollar un paquete y probar su instalación. Fíjese en que Target contiene el nombre del paquete y no el comando `install`, que se da por hecho al usar `ExecuteIn="output"`.

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);InstallMyPackage</PythonCommands>
</PropertyGroup>

<Target Name="InstallMyPackage" Label="pip install my-package" Returns="@(Commands)">
  <CreatePythonCommandItem Target="my-package" TargetType="pip" Arguments=""
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="output">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="show-outdated-pip-packages-pip-target"></a>Mostrar paquetes de pip obsoletos (Target: pip)

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);ShowOutdatedPackages</PythonCommands>
</PropertyGroup>

<Target Name="ShowOutdatedPackages" Label="Show outdated pip packages" Returns="@(Commands)">
  <CreatePythonCommandItem Target="list" TargetType="pip" Arguments="-o --format columns"
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="consolepause">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-an-executable-with-consolepause"></a>Ejecutar un archivo ejecutable con consolepause

El siguiente comando simplemente ejecuta `where` para mostrar los archivos de Python, empezando por la carpeta del proyecto:

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);ShowAllPythonFilesInProject</PythonCommands>
</PropertyGroup>

<Target Name="ShowAllPythonFilesInProject" Label="Show Python files in project" Returns="@(Commands)">
  <CreatePythonCommandItem Target="where" TargetType="executable" Arguments="/r . *.py"
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="output">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-server-and-run-debug-server-commands"></a>Comandos Iniciar servidor e Iniciar el servidor de depuración

Para saber cómo se definen los comandos **Iniciar servidor** e **Iniciar el servidor de depuración** en los proyectos web, eche un vistazo a [Microsoft.PythonTools.Web.targets](https://github.com/Microsoft/PTVS/blob/master/Python/Product/BuildTasks/Microsoft.PythonTools.Web.targets) (GitHub).

### <a name="install-package-for-development"></a>Instalar el paquete para desarrollo

```xml
<PropertyGroup>
  <PythonCommands>PipInstallDevCommand;$(PythonCommands);</PythonCommands>
</PropertyGroup>

<Target Name="PipInstallDevCommand" Label="Install package for development" Returns="@(Commands)">
    <CreatePythonCommandItem Target="pip" TargetType="module" Arguments="install --editable $(ProjectDir)"
        WorkingDirectory="$(WorkingDirectory)" ExecuteIn="Repl:Install package for development">
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

*De [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), usado con permiso.*

### <a name="generate-windows-installer"></a>Generar el instalador de Windows

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);BdistWinInstCommand;</PythonCommands>
</PropertyGroup>

<Target Name="BdistWinInstCommand" Label="Generate Windows Installer" Returns="@(Commands)">
    <CreatePythonCommandItem Target="$(ProjectDir)setup.py" TargetType="script"
        Arguments="bdist_wininst --user-access-control=force --title &quot;$(InstallerTitle)&quot; --dist-dir=&quot;$(DistributionOutputDir)&quot;"
        WorkingDirectory="$(WorkingDirectory)" RequiredPackages="setuptools"
        ExecuteIn="Repl:Generate Windows Installer">
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

*De [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), usado con permiso.*

### <a name="generate-wheel-package"></a>Generar un paquete Wheel

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);BdistWheelCommand;</PythonCommands>
</PropertyGroup>

<Target Name="BdistWheelCommand" Label="Generate Wheel Package" Returns="@(Commands)">

  <CreatePythonCommandItem Target="$(ProjectDir)setup.py" TargetType="script"
      Arguments="bdist_wheel --dist-dir=&quot;$(DistributionOutputDir)&quot;"
      WorkingDirectory="$(WorkingDirectory)" RequiredPackages="wheel;setuptools"
      ExecuteIn="Repl:Generate Wheel Package">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

*De [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), usado con permiso.*

## <a name="troubleshooting"></a>Solución de problemas

### <a name="message-the-project-file-could-not-be-loaded"></a>Mensaje: " No se pudo cargar el archivo del proyecto"

Indica que hay errores de sintaxis en el archivo de proyecto. El mensaje refleja el error específico con un número de línea y una posición de carácter.

### <a name="console-window-closes-immediately-after-command-is-run"></a>La ventana de la consola se cierra inmediatamente después de que el comando se ejecute

Use `ExecuteIn="consolepause"` en lugar de `ExecuteIn="console"`.

### <a name="command-does-not-appear-on-the-menu"></a>El comando no aparece en el menú

Compruebe que el comando está incluido en el grupo de propiedades `<PythonCommands>` y que el nombre que figura en la lista de comandos es el mismo que el nombre especificado en el elemento `<Target>`.

Por ejemplo, en el siguiente código, el nombre "Example" en el grupo de propiedades no coincide con el nombre "ExampleCommand" en el destino. Visual Studio no encuentra un comando llamado "Example", así que no se muestra ningún comando. Use "ExampleCommand" en la lista de comandos, o bien cambie el nombre del destino a sencillamente "Example".

```xml
  <PropertyGroup>
    <PythonCommands>$(PythonCommands);Example</PythonCommands>
  </PropertyGroup>
  <Target Name="ExampleCommand" Label="Example Command" Returns="@(Commands)">
    <!-- ... -->
  </Target>
```

### <a name="message-an-error-occurred-while-running-command-name-failed-to-get-command-target-name-from-project"></a>Mensaje: Error al ejecutar (nombre de comando). No se pudo obtener el comando (nombre de destino) del proyecto.

Indica que el contenido de los elementos `<Target>` o `<CreatePythonCommandItem>` es incorrecto. Esto puede deberse a lo siguiente:

- El atributo `Target` necesario está vacío.
- El atributo `TargetType` necesario está vacío o contiene un valor no reconocido.
- El atributo `ExecuteIn` necesario está vacío o contiene un valor no reconocido.
- Se ha especificado `ErrorRegex` o `WarningRegex` sin definir `ExecuteIn="output"`.
- Existen atributos no reconocidos en el elemento. Por ejemplo, puede que haya usado `Argumnets` (mal escrito) en lugar de `Arguments`.

Los valores de atributo pueden estar vacíos si se hace referencia a una propiedad que no está definida. Por ejemplo, si usa el token `$(StartupFile)`, pero no ha definido ningún archivo de inicio en el proyecto, el token se resuelve como una cadena vacía. En tales casos, conviene definir un valor predeterminado. Por ejemplo, los comandos **Iniciar servidor** e **Iniciar el servidor de depuración** definidos en las plantillas de proyecto de Bottle, Flask y Django se establecen de forma predeterminada en `manage.py` si no se ha especificado un archivo de inicio del servidor en las propiedades del proyecto.

### <a name="visual-studio-hangs-and-crashes-when-running-the-command"></a>Visual Studio se bloquea cuando el comando se ejecuta

Probablemente esté intentando ejecutar un comando de consola con `ExecuteIn="output"`, en cuyo caso Visual Studio se puede bloquear al intentar analizar la salida. Utilice `ExecuteIn="console"` en su lugar. (Vea el [problema 3682](https://github.com/Microsoft/PTVS/issues/3681)).

### <a name="executable-command-is-not-recognized-as-an-internal-or-external-command-operate-program-or-batch-file"></a>El comando ejecutable no se reconoce como un comando interno o externo, programa o archivo por lotes ejecutable

Al usar `TargetType="executable"`, el valor de `Target` debe ser *únicamente* el nombre del programa sin argumentos, como "python" o "python.exe". Mueva los argumentos que haya al atributo `Arguments`.
