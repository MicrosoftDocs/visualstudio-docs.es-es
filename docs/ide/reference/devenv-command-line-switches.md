---
title: Modificadores de línea de comandos para Devenv
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- switches, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: db9aaeb48095b058abb0deefa342598eefeed1b9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970232"
---
# <a name="devenv-command-line-switches"></a>Modificadores de línea de comandos para Devenv

Devenv le permite establecer varias opciones para el IDE, la compilación de proyectos, la depuración de proyectos y la implementación de proyectos desde la línea de comandos. Use estos modificadores para ejecutar el IDE desde un script o un archivo .bat (por ejemplo, la versión de desarrollo de un script) o para iniciar el IDE con una configuración determinada.

> [!NOTE]
> Para las tareas relacionadas con la compilación, le recomendamos usar MSBuild en lugar de devenv. Para obtener más información, vea [Referencia de la línea de comandos de MSBuild](../../msbuild/msbuild-command-line-reference.md).

Para obtener información sobre los modificadores relacionados con el desarrollo de VSPackage, vea también [Modificadores de línea de comandos de Devenv para el desarrollo de VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md).

## <a name="devenv-switch-syntax"></a>Sintaxis de los modificadores de Devenv

La utilidad `devenv.com` controla los comandos que comienzan por `devenv`, que ofrece salida a través de secuencias del sistema estándar, como `stdout` y `stderr`. La utilidad determina la redirección de E/S adecuada al capturar el resultado, por ejemplo a un archivo .txt.

Por otro lado, los comandos que empiezan por `devenv.exe` pueden usar los mismos modificadores, pero se omite la utilidad `devenv.com`. El uso de `devenv.exe` directamente impide que la salida aparezca en la consola.

Las reglas de sintaxis de los modificadores de `devenv` son similares a las de otras utilidades de la línea de comandos de DOS. Las siguientes reglas sintácticas se aplican a todos los modificadores de `devenv` y sus argumentos:

- Los comandos comienzan por `devenv`.

- Los modificadores no distinguen mayúsculas de minúsculas.

- Puede especificar un modificador con un guion ("-") o una barra diagonal ("/").

- Cuando se especifica una solución o un proyecto, el primer argumento es el nombre del archivo de solución o del archivo de proyecto, incluida la ruta de acceso del archivo.

- Si el primer argumento es un archivo que no es una solución ni un proyecto, el archivo se abrirá en el editor adecuado, en una instancia nueva del IDE.

- Cuando se indica un nombre de archivo de proyecto en lugar de un nombre de archivo de solución, un comando `devenv` busca en la carpeta primaria del archivo de proyecto un archivo de solución que tenga el mismo nombre. Por ejemplo, el comando `devenv myproject1.vbproj /build` busca en la carpeta principal un archivo de solución denominado `myproject1.sln`.

  > [!NOTE]
  > En su carpeta primaria debe haber un archivo de solución, y solamente uno, que haga referencia a este proyecto. Si la carpeta primaria no contiene ningún archivo de solución que haga referencia a este proyecto, o si contiene dos o más archivos de solución que hagan referencia a él, se crea un archivo de solución temporal.

- Si las rutas de acceso y los nombres de archivo contienen espacios en blanco, se deben incluir entre comillas dobles (""). Por ejemplo: `"c:\project a\"`.

- Inserte un carácter de espacio entre los modificadores y los argumentos de la misma línea. Por ejemplo, el comando `devenv /log output.txt` abre el IDE y envía toda la información de registro de esa sesión a output.txt.

- No se puede usar la sintaxis de coincidencia de patrones en los comandos de `devenv`.

## <a name="devenv-switches"></a>Modificadores de devenv

Los siguientes modificadores de línea de comandos muestran el IDE y realizan la tarea descrita.

|Modificador de la línea de comandos|Descripción|
| - |-----------------|
|[/Command](command-devenv-exe.md)|Inicia el IDE y ejecuta el comando especificado.<br /><br /> `devenv /command "nav https://docs.microsoft.com/"`|
|[/DebugExe](debugexe-devenv-exe.md)|Carga un archivo ejecutable de C++ bajo el control del depurador. Este modificador no está disponible para los archivos ejecutables de Visual Basic o C#. Para obtener más información, vea [Iniciar automáticamente un proceso en el depurador](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).<br /><br /> `devenv /debugexe mysln.exe`|
|[/Diff](diff.md)|Compara dos archivos. Toma cuatro parámetros: *SourceFile*, *TargetFile*, *SourceDisplayName* (opcional) y *TargetDisplayName* (opcional).<br /><br /> `devenv /diff File1 File2 Alias1 Alias2`|
|[/DoNotLoadProjects](donotloadprojects-devenv-exe.md)|Abre la solución especificada sin cargar ningún proyecto.<br /><br /> `devenv /donotloadprojects mysln.sln`|
|[/Edit](edit-devenv-exe.md)|Abre los archivos especificados en una instancia en ejecución de esta aplicación. Si no hay ninguna instancia en ejecución, inicia una instancia nueva con un diseño de ventanas simplificado.<br /><br /> `devenv /edit File1 File2`|
|[/LCID o /L](lcid-devenv-exe.md)|Establece el idioma predeterminado del IDE. Si el idioma especificado no se incluye en la instalación de Visual Studio, se omitirá este valor.<br /><br /> `devenv /l 1033`|
|[/Log](log-devenv-exe.md)|Inicia Visual Studio y registra toda la actividad en el archivo de registro.<br /><br /> `devenv /log mylogfile.xml`|
|[/NoSplash](nosplash-devenv-exe.md)|Abre el IDE sin mostrar la pantalla de presentación.<br /><br /> `devenv /nosplash File1 File2`|
|[/Run o /R](run-devenv-exe.md)|Compila y ejecuta la solución especificada.<br /><br /> `devenv /run mysln.sln`|
|[/RunExit](runexit-devenv-exe.md)|Compila y ejecuta la solución especificada, minimiza el IDE cuando se ejecuta la solución y cierra el IDE una vez finalizada la ejecución de la solución.<br /><br /> `devenv /runexit mysln.sln`|
|[/SafeMode](safemode-devenv-exe.md)|Inicia Visual Studio en modo seguro. Este modificador carga únicamente el entorno predeterminado, los servicios predeterminados y las versiones publicadas de paquetes de terceros.<br /><br /> Este modificador no toma ningún argumento.|
|[/UseEnv](useenv-devenv-exe.md)|Hace que el IDE use las variables de entorno PATH, INCLUDE, LIBPATH y LIB para la compilación de C++. Este modificador se instala con la carga de trabajo **Desarrollo para el escritorio con C++**. Para obtener más información, vea [Establecer la ruta de acceso y las variables de entorno para compilar desde la línea de comandos](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds).|

Los siguientes modificadores de línea de comandos no muestran el IDE.

|Modificador de la línea de comandos|Descripción|
| - |-----------------|
|[/?](q-devenv-exe.md)|Muestra la ayuda para los modificadores de `devenv` en la **ventana del símbolo del sistema**.<br /><br /> Este modificador no toma ningún argumento.|
|[/Build](build-devenv-exe.md)|Compila la solución o el proyecto especificado según la configuración de la solución especificada.<br /><br /> `devenv mysln.sln /build`|
|[/Clean](clean-devenv-exe.md)|Elimina los archivos creado por el comando de compilación, sin afectar a los archivos de código fuente.<br /><br /> `devenv mysln.sln /clean`|
|[/Deploy](deploy-devenv-exe.md)|Compila la solución con los archivos necesarios para la implementación, según la configuración de la solución.<br /><br /> `devenv mysln.sln /deploy`|
|[/Out](out-devenv-exe.md)|Permite especificar un archivo para recibir los errores al compilar.<br /><br /> `devenv mysln.sln /build Debug /out log.txt`|
|[/Project](project-devenv-exe.md)|Proyecto que se va a compilar, limpiar o implementar. Puede usar este modificador únicamente si también ha especificado el modificador `/Build`, `/Rebuild`, `/Clean` o `/Deploy`.<br /><br /> `devenv mysln.sln /build Debug /project proj1`|
|[/ProjectConfig](projectconfig-devenv-exe.md)|Especifica la configuración de proyecto que se va a compilar o implementar. Puede usar este modificador únicamente si también ha especificado el modificador `/Project`.<br /><br /> `devenv mysln.sln /build Release /project proj1 /projectconfig Release`|
|[/Rebuild](rebuild-devenv-exe.md)|Limpia y, a continuación, compila la solución o el proyecto especificado según la configuración de la solución especificada.<br /><br /> `devenv mysln.sln /rebuild`|
|[/ResetSettings](resetsettings-devenv-exe.md)|Restaura la configuración predeterminada de Visual Studio. Opcionalmente, restablece la configuración del archivo `.vssettings` especificado.<br /><br /> `devenv /resetsettings mysettings.vssettings`|
|[/Upgrade](upgrade-devenv-exe.md)|Actualiza el archivo de solución especificado y todos sus archivos de proyecto, o bien el archivo de proyecto especificado, a los formatos actuales de Visual Studio para estos archivos.<br /><br /> `devenv mysln.sln /upgrade`|

## <a name="see-also"></a>Vea también

- [General, Entorno, Opciones (Cuadro de diálogo)](general-environment-options-dialog-box.md)
- [Modificadores de línea de comandos Devenv para el desarrollo de VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
