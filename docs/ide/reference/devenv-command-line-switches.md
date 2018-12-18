---
title: Modificadores de línea de comandos para Devenv de Visual Studio
ms.date: 02/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- switches, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 818bbb38fab706dde2f4d36d5a534e0a351a6450
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948899"
---
# <a name="devenv-command-line-switches"></a>Modificadores de línea de comandos para Devenv

Devenv permite establecer diversas opciones para el entorno de desarrollo integrado (IDE), así como compilar, depurar e implementar proyectos, desde la línea de comandos. Use estos modificadores para ejecutar el IDE desde un script o un archivo .bat (por ejemplo, un script de compilación nocturna) o para iniciar el IDE con una configuración determinada.

> [!NOTE]
> Para las tareas relacionadas con la compilación, se recomienda usar MSBuild en lugar de devenv. Para obtener más información, vea [Referencia de la línea de comandos de MSBuild](../../msbuild/msbuild-command-line-reference.md).

## <a name="devenv-switch-syntax"></a>Sintaxis de los modificadores de Devenv

La utilidad `devenv.com` controla los comandos que comienzan por `devenv`, que ofrece salida a través de secuencias del sistema estándar, como `stdout` y `stderr`. La utilidad determina la redirección de E/S adecuada al capturar el resultado, por ejemplo a un archivo .txt.

Por otro lado, los comandos que comienzan por `devenv.exe` pueden usar los mismos modificadores, pero se omite la utilidad `devenv.com`. El uso de `devenv.exe` directamente impide que la salida aparezca en la consola.

Las reglas de sintaxis de los modificadores de `devenv` son similares a las de otros programas de línea de comandos de DOS. Las siguientes reglas sintácticas se aplican a todos los modificadores de `devenv` y sus argumentos:

- Los comandos comienzan por `devenv`.

- Los modificadores no distinguen mayúsculas de minúsculas.

- Cuando se especifica una solución o un proyecto, el primer argumento es el nombre del archivo de solución o del archivo de proyecto, incluida la ruta de acceso del archivo.

- Si el primer argumento es un archivo que no es una solución ni un proyecto, ese archivo se abre en el editor adecuado, en una instancia nueva del IDE.

- Cuando se indica un nombre de archivo de proyecto en lugar de un nombre de archivo de solución, un comando `devenv` busca en la carpeta primaria del archivo de proyecto un archivo de solución que tenga el mismo nombre. Por ejemplo, el comando `devenv myproject1.vbproj /build` busca en la carpeta primaria un archivo de solución denominado "myproject1.sln".

    > [!NOTE]
    > En su carpeta primaria debe haber un archivo de solución, y solamente uno, que haga referencia a este proyecto. Si la carpeta primaria no contiene ningún archivo de solución que haga referencia a este proyecto, o si contiene dos o más archivos de solución que hagan referencia a él, se crea un archivo de solución temporal.

- Si las rutas de acceso y los nombres de archivo contienen espacios en blanco, se deben incluir entre comillas dobles (""). Por ejemplo, "c:\project a\\".

- Inserte un carácter de espacio entre los modificadores y los argumentos de la misma línea. Por ejemplo, el comando **devenv /log output.txt** abre el IDE y envía toda la información de registro de esa sesión a output.txt.

- No se puede utilizar la sintaxis de coincidencia de patrones en los comandos de `devenv`.

## <a name="devenv-switches"></a>Modificadores de devenv

Los modificadores de línea de comandos siguientes muestran el IDE y realizan la tarea descrita.

|Modificador de la línea de comandos|Descripción|
| - |-----------------|
|[/Command](../../ide/reference/command-devenv-exe.md)|Inicia el IDE y ejecuta el comando especificado.|
|[/DebugExe](../../ide/reference/debugexe-devenv-exe.md)|Carga un archivo ejecutable de C++ bajo el control del depurador. Este modificador no está disponible para los archivos ejecutables de Visual Basic o C#. Para obtener más información, vea [Iniciar automáticamente un proceso en el depurador](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).|
|[/LCID o /l](../../ide/reference/lcid-devenv-exe.md)|Establece el idioma predeterminado del IDE. Si el idioma especificado no está incluido en la instalación de Visual Studio, este valor se omite.|
|[/Log](../../ide/reference/log-devenv-exe.md)|Inicia Visual Studio y registra toda la actividad en el archivo de registro.|
|[/Run o /r](../../ide/reference/run-devenv-exe.md)|Compila y ejecuta la solución especificada.|
|[/Runexit](../../ide/reference/runexit-devenv-exe.md)|Compila y ejecuta la solución especificada, minimiza el IDE cuando se ejecuta la solución y cierra el IDE una vez finalizada la ejecución de la solución.|
|[/UseEnv](../../ide/reference/useenv-devenv-exe.md)|Hace que el IDE use las variables de entorno PATH, INCLUDE y LIB para la compilación de C++ en lugar de la configuración especificada en la sección Directorios de VC++ de las opciones de **Proyectos** del cuadro de diálogo **Opciones**. Este modificador se instala con la carga de trabajo **Desarrollo para el escritorio con C++**. Para obtener más información, vea [Establecer la ruta de acceso y las variables de entorno para compilar desde la línea de comandos](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds).|
|[/Edit](../../ide/reference/edit-devenv-exe.md)|Abre los archivos especificados en una instancia en ejecución de esta aplicación. Si no hay ninguna instancia en ejecución, inicia una instancia nueva con un diseño de ventanas simplificado.|
|[/SafeMode](../../ide/reference/safemode-devenv-exe.md)|Inicia Visual Studio en modo seguro y solo carga el entorno y los servicios predeterminados, así como las versiones de paquetes de terceros suministradas.|
|[/ResetSkipPkgs](../../ide/reference/resetskippkgs-devenv-exe.md)|Borra todas las etiquetas SkipLoading agregadas a VSPackages por usuarios que desean evitar problemas al cargar VSPackages.|
|[/Setup](../../ide/reference/setup-devenv-exe.md)|Fuerza a Visual Studio a fusionar mediante combinación los metadatos de recursos que describen los menús, las barras de herramientas y los grupos de comandos de todos los VSPackages disponibles. Debe ejecutar este comando como administrador.|

Los modificadores de la línea de comandos siguientes no muestran el IDE.

|Modificador de la línea de comandos|Descripción|
| - |-----------------|
|[/?](../../ide/reference/q-devenv-exe.md)|Muestra ayuda para los modificadores de devenv en la **ventana de símbolo del sistema**.<br /><br /> `devenv /?`|
|[/Build](../../ide/reference/build-devenv-exe.md)|Compila la solución o el proyecto especificado según la configuración de la solución especificada.<br /><br /> `devenv myproj.csproj /build`|
|[/Clean](../../ide/reference/clean-devenv-exe.md)|Elimina los archivos creado por el comando de compilación, sin afectar a los archivos de código fuente.<br /><br /> `devenv myproj.csproj /clean`|
|[/Deploy](../../ide/reference/deploy-devenv-exe.md)|Compila la solución, junto con los archivos necesario para la implementación, según la configuración de soluciones.<br /><br /> `devenv myproj.csproj /deploy`|
|[/Diff](../../ide/reference/diff.md)|Compara dos archivos. Toma cuatro parámetros: SourceFile, TargetFile, SourceDisplayName (opcional) y TargetDisplayName (opcional).|
|[/Out](../../ide/reference/out-devenv-exe.md)|Permite especificar un archivo para recibir los errores al compilar.<br /><br /> `devenv myproj.csproj /build /out log.txt`|
|[/Project](../../ide/reference/project-devenv-exe.md)|Proyecto que se va a compilar, limpiar o implementar. Solo se puede utilizar este modificador si también se ha indicado el modificador /build, /rebuild, /clean o /deploy.|
|[/ProjectConfig](../../ide/reference/projectconfig-devenv-exe.md)|Especifica la configuración de proyecto que se va a compilar o implementar. Solo se puede utilizar este modificador si también se ha indicado el modificador /project.|
|[/Rebuild](../../ide/reference/rebuild-devenv-exe.md)|Limpia y, a continuación, compila la solución o el proyecto especificado según la configuración de la solución especificada.|
|[/ResetSettings](../../ide/reference/resetsettings-devenv-exe.md)|Restaura la configuración predeterminada de Visual Studio. Opcionalmente, restablece la configuración del archivo .vssettings especificado.|
|[/Upgrade](../../ide/reference/upgrade-devenv-exe.md)|Actualiza el archivo de solución especificado y todos sus archivos de proyecto, o bien el archivo de proyecto especificado, a los formatos actuales de Visual Studio para estos archivos.|

## <a name="see-also"></a>Vea también

* [General, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md)
