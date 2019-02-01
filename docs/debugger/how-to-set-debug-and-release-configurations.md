---
title: Debug y release configuraciones | Microsoft Docs
ms.date: 10/05/2018
ms.topic: reference
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
ms.openlocfilehash: 1e4c1c12409d89d88e683cd0e5b39a8d5a5459df
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54969777"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Establecer configuraciones Debug y Release en Visual Studio

Los proyectos de Visual Studio tienen configuraciones independientes para el lanzamiento y la depuración del programa. Compile la versión de depuración para la depuración y la versión de lanzamiento para la distribución de la versión final.

En la configuración de depuración, el programa se compile con información de depuración simbólica completa y sin optimización. La optimización complica la depuración, ya que la relación entre el código fuente y las instrucciones generadas es más compleja.

La configuración de lanzamiento del programa no tiene ninguna información de depuración simbólica y está totalmente optimizada. Para código administrado y código de C++, se puede generar información de depuración en los archivos .pdb, [según las opciones del compilador](#BKMK_symbols_release) que se usan. Creación de los archivos .pdb puede ser útil si luego necesita depurar la versión de lanzamiento.

Para más información sobre las configuraciones de compilación, vea [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md).

La configuración de compilación se puede modificar desde el menú **Compilar**, la barra de herramientas o las páginas de propiedades del proyecto. Las páginas de propiedades del proyecto son específicas de un lenguaje. El procedimiento que se indica a continuación muestra cómo cambiar la configuración de compilación desde el menú y la barra de herramientas. Para obtener más información sobre cómo cambiar la configuración de compilación en proyectos en distintos lenguajes, consulte el [Vea también](#see-also) sección más adelante.

## <a name="change-the-build-configuration"></a>Cambiar la configuración de compilación

Para cambiar la configuración de compilación, ya sea:

* Desde el **compilar** menú, seleccione **Configuration Manager**, a continuación, seleccione **depurar** o **versión**.

o

* En la barra de herramientas, elija **Depurar** o **Versión** en el cuadro de lista **Configuraciones de soluciones**.

  ![las barras de herramientas de configuración de compilación](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")

## <a name="BKMK_symbols_release"></a>Generar archivos de símbolos (.pdb) para una compilación (C#, C++, Visual Basic, F#)

Puede elegir generar archivos de símbolos (.pdb) y qué incluir información de depuración. Para la mayoría de los tipos de proyecto, el compilador genera archivos de símbolos de forma predeterminada para la depuración y lanzamiento, mientras que otras configuraciones predeterminadas difieren según el tipo de proyecto y la versión de Visual Studio.

> [!IMPORTANT]
> El depurador solo cargará un archivo .pdb de un archivo ejecutable que coincida exactamente con el archivo .pdb creado cuando se compiló el archivo ejecutable (es decir, el archivo .pdb debe ser el original o una copia del archivo .pdb original). Para obtener más información, vea [Why does Visual Studio require debugger symbol files to *exactly* match the binary files that they were built with?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/) ¿Por qué Visual Studio requiere que los archivos de símbolo del depurador coincidan exactamente con los archivos binarios con los que se crearon?

Cada tipo de proyecto puede tener una forma diferente de la configuración de estas opciones.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Generar archivos de símbolos para un proyecto de C#, ASP.NET o Visual Basic

Para obtener información detallada sobre la configuración del proyecto para configuraciones de depuración en C# o Visual Basic, vea [configuración de proyectos para una C# configuración de depuración](../debugger/project-settings-for-csharp-debug-configurations.md) o [configuración de proyectos para una depuración de Visual Basic configuración](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. En el Explorador de soluciones, seleccione el proyecto.

2. Seleccione el **propiedades** icono (o presione **ALT+ENTRAR**).

3. En el panel lateral, elija **compilar** (o **compilar** en Visual Basic).

4. En el **configuración** elija **depurar** o **versión**.

5. Seleccione el **avanzadas** botón (o la **Advanced Compile Options** botón en Visual Basic).

6. En el **información de depuración** lista (o el **generar información de depuración** lista en Visual Basic), elija **completa**, **solo Pdb**, o **Portable**.

   El formato portable es el más reciente multiplataforma para .NET Core. Para obtener más información sobre las opciones, consulte [cuadro de diálogo de configuración de compilación avanzada (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

   ![Generar archivos PDB para las compilaciones en C#](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

7. Compilar el proyecto.

   El compilador crea los archivos de símbolos en la misma carpeta que el ejecutable o el archivo de salida principal.

### <a name="generate-symbol-files-for-a-c-project"></a>Generar archivos de símbolos para un proyecto de C++

1. En el Explorador de soluciones, seleccione el proyecto.

2. Seleccione el **propiedades** icono (o presione **ALT+ENTRAR**).

3. En el **configuración** elija **depurar** o **versión**.

4. En el panel lateral, elija **vinculador > depuración**, seleccione las opciones de **generar información de depuración**.

   Para obtener información detallada sobre la configuración del proyecto para configuraciones de depuración en C++, vea [configuración del proyecto para C++ debug configuration](../debugger/project-settings-for-a-cpp-debug-configuration.md).

5. Configurar las opciones de **generar archivos de base de datos de programa**.

   En la mayoría de los proyectos de C++, el valor predeterminado es `$(OutDir)$(TargetName).pdb`, que genera archivos .pdb en la carpeta de salida.

   ![Generar archivos PDB para las compilaciones en C++](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus")

6. Compilar el proyecto.

   El compilador crea los archivos de símbolos en la misma carpeta que el ejecutable o el archivo de salida principal.

## <a name="see-also"></a>Vea también
 
[Especificar archivos de símbolos (.pdb) y archivos de origen en el depurador de Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)<br/>
[Preparación y configuración del depurador](../debugger/debugger-settings-and-preparation.md)<br/>
[Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)<br/>
[Configuración del proyecto para una configuración de depuración de C#](../debugger/project-settings-for-csharp-debug-configurations.md)<br/>
[Configuración de proyectos para una configuración de depuración en Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)<br/>
[Cómo: Crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md)
