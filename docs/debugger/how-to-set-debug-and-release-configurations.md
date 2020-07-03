---
title: Establecimiento de configuraciones de depuración y versión | Microsoft Docs
ms.date: 10/05/2018
ms.topic: how-to
f1_keywords:
- vs.debug.builds
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- configurations, release
- build configurations, release
- projects [Visual Studio], release configurations
- debugging [Visual Studio], release configurations
- release builds, changing settings
- debug builds
- debug builds, switching to release build
- debug builds, changing configuration settings
- debugging [Visual Studio], debug configurations
- projects [Visual Studio], debug configurations
- build configurations, debug
- debug configurations
- release builds, switching to debug build
- Visual Basic projects, debug and release builds
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 458e6cb4ebf882d2d9e331823cc4955143e7d5b7
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349164"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Establecer configuraciones Debug y Release en Visual Studio

Los proyectos de Visual Studio tienen configuraciones independientes para el lanzamiento y la depuración del programa. La versión de depuración se compila para depurar y la versión de lanzamiento para la distribución final.

En la configuración de depuración, el programa se compila sin optimizar y con toda la información de depuración simbólica. La optimización complica la depuración, ya que la relación entre el código fuente y las instrucciones generadas es más compleja.

La configuración de versión del programa no contiene información de depuración simbólica y está totalmente optimizada. Para código administrado y de C++, la información de depuración se puede generar en archivos .pdb, [en función de las opciones del compilador](#BKMK_symbols_release) que se usen. La creación de archivos .pdb puede ser útil si más tarde tiene que depurar la versión de lanzamiento.

Para más información sobre las configuraciones de compilación, vea [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md).

La configuración de compilación se puede modificar desde el menú **Compilar**, la barra de herramientas o las páginas de propiedades del proyecto. Las páginas de propiedades del proyecto son específicas de un lenguaje. El procedimiento que se indica a continuación muestra cómo cambiar la configuración de compilación desde el menú y la barra de herramientas. Para obtener más información sobre cómo cambiar la configuración de compilación de proyectos en distintos lenguajes, vea la sección [Vea también](#see-also) más adelante.

## <a name="change-the-build-configuration"></a>Cambio de la configuración de compilación

Para cambiar la configuración de compilación:

* En el menú **Compilar**, seleccione **Administrador de configuración** y después **Depurar** o **Versión**.

o

* En la barra de herramientas, elija **Depurar** o **Versión** en el cuadro de lista **Configuraciones de soluciones**.

  ![Configuración de compilación de las barras de herramientas](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")

## <a name="generate-symbol-pdb-files-for-a-build-c-c-visual-basic-f"></a><a name="BKMK_symbols_release"></a>Generación de archivos de símbolos (.pdb) para una compilación (C#, C++, Visual Basic, F#)

Puede optar por generar archivos de símbolos (.pdb) y la información de depuración que se va a incluir. Para la mayoría de los tipos de proyecto, el compilador genera archivos de símbolos de forma predeterminada para las compilaciones de depuración y versión, mientras que otros valores predeterminados varían según el tipo de proyecto y la versión de Visual Studio.

> [!IMPORTANT]
> El depurador solo cargará un archivo .pdb de un archivo ejecutable que coincida exactamente con el archivo .pdb creado cuando se compiló el archivo ejecutable (es decir, el archivo .pdb debe ser el original o una copia del archivo .pdb original). Para obtener más información, vea [¿Por qué Visual Studio requiere que los archivos de símbolos del depurador coincidan exactamente con los archivos binarios con los que se han creado?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/).

Cada tipo de proyecto puede tener una manera distinta de establecer estas opciones.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Generación de archivos de símbolos para un proyecto de C#, ASP.NET o Visual Basic

Para obtener más información sobre la configuración del proyecto para configuraciones de depuración en C# o Visual Basic, vea [Configuración del proyecto para una configuración de depuración de C#](../debugger/project-settings-for-csharp-debug-configurations.md) o [Configuración del proyecto para una configuración de depuración de Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. En el Explorador de soluciones, seleccione el proyecto.

2. Seleccione el icono **Propiedades** (o presione **Alt+Entrar**).

3. En el panel lateral, elija **Compilar** (o **Compilar** en Visual Basic).

4. En la lista **Configuración**, elija **Depurar** o **Versión**.

5. Seleccione el botón **Avanzado** (o el botón **Opciones de compilación avanzadas** de Visual Basic).

6. En la lista **Información de depuración** (o la lista **Generar información de depuración** de Visual Basic), elija **Completa**, **Solo PDB** o **Portátil**.

   El formato portátil es el formato multiplataforma más reciente para .NET Core. Para obtener más información sobre las opciones, vea [Cuadro de diálogo Configuración de compilación avanzada (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

   ![Generación de archivos PDB para compilaciones en C#](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

7. Compilar el proyecto.

   El compilador crea los archivos de símbolos en la misma carpeta que el ejecutable o el archivo de salida principal.

### <a name="generate-symbol-files-for-a-c-project"></a>Generación de archivos de símbolos para un proyecto de C++

1. En el Explorador de soluciones, seleccione el proyecto.

2. Seleccione el icono **Propiedades** (o presione **Alt+Entrar**).

3. En la lista **Configuración**, elija **Depurar** o **Versión**.

4. En el panel lateral, elija **Enlazador > Depuración** y, después, seleccione opciones para **Generar información de depuración**.

   Para obtener información detallada sobre la configuración del proyecto para las configuraciones de depuración en C++, vea [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

5. Configure las opciones de **Generar archivos de base de datos de programa**.

   En la mayoría de los proyectos de C++, el valor predeterminado es `$(OutDir)$(TargetName).pdb`, que genera archivos .pdb en la carpeta de salida.

   ![Generación de archivos PDB para compilaciones en C++](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus")

6. Compilar el proyecto.

   El compilador crea los archivos de símbolos en la misma carpeta que el ejecutable o el archivo de salida principal.

## <a name="see-also"></a><a name="see-also"></a>Vea también

- [Especificación de archivos de código fuente y símbolos (.pdb) en el depurador de Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)<br/>
- [Preparación y configuración del depurador](../debugger/debugger-settings-and-preparation.md)<br/>
- [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)<br/>
- [Configuración del proyecto para una configuración de depuración de C#](../debugger/project-settings-for-csharp-debug-configurations.md)<br/>
- [Configuración de proyectos para una configuración de depuración en Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)<br/>
- [Cómo: Crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md)
