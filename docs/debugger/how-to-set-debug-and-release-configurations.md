---
title: Debug y release configuraciones | Microsoft Docs
ms.custom: ''
ms.date: 10/05/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 18689a82fe2ae7c66eb8e8d6ef9bd115e2950cac
ms.sourcegitcommit: 50b19010b2e2b4736835350710e2edf93b980b56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/10/2018
ms.locfileid: "49073999"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Debug y release configuraciones en Visual Studio

Los proyectos de Visual Studio tienen configuraciones independientes para el lanzamiento y la depuración del programa. Compile la versión de depuración para la depuración y la versión de lanzamiento para la distribución de la versión final.

En la configuración de depuración, el programa se compile con información de depuración simbólica completa y sin optimización. La optimización complica la depuración, ya que la relación entre el código fuente y las instrucciones generadas es más compleja.

La configuración de lanzamiento del programa no tiene ninguna información de depuración simbólica y está totalmente optimizada. Depurar se puede generar información de los archivos .pdb, [según las opciones del compilador](#BKMK_symbols_release) que se usan. Creación de los archivos .pdb puede ser útil si luego necesita depurar la versión de lanzamiento.

Para más información sobre las configuraciones de compilación, vea [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md).

Puede cambiar la configuración de compilación desde el **compilar** menú desde la barra de herramientas, o en páginas de propiedades del proyecto. Las páginas de propiedades del proyecto son específicas de un lenguaje. El procedimiento que se indica a continuación muestra cómo cambiar la configuración de compilación desde el menú y la barra de herramientas. Para obtener más información sobre cómo cambiar la configuración de compilación en proyectos en distintos lenguajes, consulte el [Vea también](#see-also) sección más adelante.

## <a name="change-the-build-configuration"></a>Cambiar la configuración de compilación

Para cambiar la configuración de compilación, ya sea:

* Desde el **compilar** menú, seleccione **Configuration Manager**, a continuación, seleccione **depurar** o **versión**.

o

* En la barra de herramientas, elija **depurar** o **versión** desde el **configuraciones de soluciones** lista.

  ![las barras de herramientas de configuración de compilación](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")

## <a name="BKMK_symbols_release"></a>Generar archivos de símbolos (.pdb) para una compilación

Puede elegir generar archivos de símbolos (.pdb) y qué incluir información de depuración. Para la mayoría de los tipos de proyecto, el compilador genera archivos de símbolos de forma predeterminada para la depuración y lanzamiento, mientras que otras configuraciones predeterminadas difieren según el tipo de proyecto y la versión de Visual Studio.

> [!IMPORTANT]
> El depurador solo cargará un archivo .pdb de un archivo ejecutable que coincida exactamente con el archivo .pdb creado cuando se compiló el archivo ejecutable (es decir, el archivo .pdb debe ser el original o una copia del archivo .pdb original). Para obtener más información, consulte [¿por qué Visual Studio requiere archivos de símbolos del depurador para ajustarse exactamente a los archivos binarios que se compilaron con?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

Cada tipo de proyecto puede tener una forma diferente de la configuración de estas opciones.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Generar archivos de símbolos para un proyecto de C#, ASP.NET o Visual Basic

Para obtener información detallada sobre la configuración del proyecto para configuraciones de depuración en C# o Visual Basic, vea [configuración de depuración de la configuración del proyecto de C#](../debugger/project-settings-for-csharp-debug-configurations.md) o [deconfiguracióndedepuracióndelaconfiguracióndelproyectodeVisualBasic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

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
