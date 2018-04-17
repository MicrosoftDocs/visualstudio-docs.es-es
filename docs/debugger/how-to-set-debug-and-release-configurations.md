---
title: 'Cómo: establecer la depuración y configuración de lanzamiento | Documentos de Microsoft'
ms.custom: H1HackMay2017
ms.date: 04/10/2017
ms.technology:
- vs-ide-debug
ms.topic: conceptual
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
ms.openlocfilehash: e85c89049c53bb097dd8a4ec850df6e66f902803
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-set-debug-and-release-configurations-in-visual-studio"></a>Cómo: establecer la depuración y liberar configuraciones en Visual Studio
Los proyectos de Visual Studio tienen configuraciones independientes para el lanzamiento y la depuración del programa. Como se desprende de sus nombres, la versión de depuración se compila para depurar y la versión de lanzamiento para la distribución final.  
  
La configuración de depuración del programa se compila sin optimizar y con toda la información de depuración simbólica. La optimización complica la depuración, ya que la relación entre el código fuente y las instrucciones generadas es más compleja.  
  
La configuración de lanzamiento del programa no contiene información de depuración simbólica y está totalmente optimizada. Depurar información puede generarse en archivos .pdb, [según las opciones del compilador](#BKMK_symbols_release) que se usan. Crear archivos PDB puede ser muy útil si luego necesita depurar la versión de lanzamiento.  
  
Para más información sobre las configuraciones de compilación, vea [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md).  
  
Puede cambiar la configuración de compilación de la **generar** menú, desde la barra de herramientas, o en páginas de propiedades del proyecto. Las páginas de propiedades del proyecto son específicas de un lenguaje. El procedimiento que se indica a continuación muestra cómo cambiar la configuración de compilación desde el menú y la barra de herramientas. Para obtener más información sobre cómo cambiar la configuración de compilación de proyectos en distintos idiomas, consulte la sección Vea también.  
  
## <a name="change-the-build-configuration"></a>Cambiar la configuración de compilación  
  
1.  Desde el **generar** menú, seleccione **Configuration Manager**, a continuación, seleccione **depurar** o **versión**.  
  
2.  En la barra de herramientas, elegir **depurar** o **versión** desde el **configuraciones de soluciones** cuadro de lista.  
  
     ![configuración de compilación de la barra de herramientas](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Esta barra de herramientas no está disponible en las ediciones Express. Puede usar el **compilar solución F6** y **Iniciar depuración F5** elementos de menú para elegir la configuración.

## <a name="BKMK_symbols_release"></a>Generar archivos de símbolos (.pbd) para una compilación

Para la mayoría de los tipos de proyecto, los archivos .pdb se generan de forma predeterminada para la depuración y de lanzamiento, pero los valores predeterminados son diferentes según el tipo de proyecto específico y la versión de Visual Studio. Puede configurar si el compilador genera archivos .pdb y qué tipo de información de depuración que se va a incluir.

> [!IMPORTANT] 
> El depurador solo cargará un archivo .pdb de un archivo ejecutable que coincida exactamente con el archivo .pdb creado cuando se compiló el archivo ejecutable (es decir, el archivo .pdb debe ser el original o una copia del archivo .pdb original). Para obtener más información, consulte [Why does Visual Studio require debugger symbol files to *exactly* match the binary files that they were built with?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

Cada tipo de proyecto puede tener una forma diferente de establecer estas opciones.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Generar archivos de símbolos para un proyecto de C#, ASP.NET o Visual Basic

Para obtener información detallada sobre la configuración del proyecto para configuraciones de depuración en C#, vea [configuración para una configuración de depuración de C# del proyecto](../debugger/project-settings-for-csharp-debug-configurations.md). En Visual Basic, consulte [en este tema](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. Haga clic en el proyecto en el Explorador de soluciones y elija **propiedades**.

2. Elija un **versión** o **depurar** construido a partir de la **configuración** lista.

2. Elija **generar** configuración y, a continuación, haga clic en el **avanzadas** botón.

    En Visual Basic, elija la **compilar** configuración y la **opciones de compilación avanzadas** botón en su lugar.

3. Elija **completa**, **portable**, o **pdb_only** en el **información de depuración** cuadro de lista (**generar información de depuración** en Visual Basic).

    El formato portable es el formato más reciente de multiplataforma para .NET Core. Para obtener más información sobre las opciones, consulte [cuadro de diálogo de configuración de compilación avanzada (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

    ![Generar archivos PDB para las compilaciones en C#](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

4. Compilar el proyecto.

    Los archivos de símbolos se crean en la misma carpeta que el archivo ejecutable o el archivo de salida principal.

### <a name="generate-symbol-files-for-a-c-project"></a>Generar archivos de símbolos para un proyecto de C++

1. Haga clic en el proyecto en el Explorador de soluciones y elija **propiedades**.

2. Elija un **versión** o **depurar** construido a partir de la **configuración** lista.

2. En **vinculador > depuración**, seleccione las opciones para la que desee **generar información de depuración**.

    Para obtener información detallada sobre la configuración del proyecto para configuraciones de depuración de C++, vea [configuración de proyectos para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

4. Configurar las opciones para generar archivos de base de datos de programa

    En la mayoría de los proyectos de C++, el valor predeterminado es `$(OutDir)$(TargetName).pdb`, lo cual genera archivos .pdb en la carpeta de salida.

    ![Generar archivos PDB para las compilaciones en C++](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus") 

5. Compilar el proyecto.

    Los archivos de símbolos se crean en la misma carpeta que el archivo ejecutable o el archivo de salida principal.
  
## <a name="see-also"></a>Vea también  
 [Especificar archivos de símbolos (.pdb) y archivos de código fuente en el depurador Visua Studio](../debugger/debugger-settings-and-preparation.md)  
 [Preparación y configuración de la depuración](../debugger/debugger-settings-and-preparation.md)   
 [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Configuración de proyectos para configuraciones de depuración en C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Configuración de proyectos para una configuración de depuración en Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Cómo: Crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md)