---
title: Establecer configuraciones de depuración y lanzamiento | Microsoft Docs
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
ms.openlocfilehash: 75acf0a3a821b4d2561ea14e583e71761b8b476e
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925470"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Establecer configuraciones Debug y Release en Visual Studio

Los proyectos de Visual Studio tienen configuraciones independientes para el lanzamiento y la depuración del programa. Compile la versión de depuración para la depuración y la versión de lanzamiento para la distribución final de la versión.

En la configuración de depuración, el programa se compila con toda la información de depuración simbólica y sin optimización. La optimización complica la depuración, ya que la relación entre el código fuente y las instrucciones generadas es más compleja.

La configuración de lanzamiento del programa no tiene información de depuración simbólica y está totalmente optimizada. En el código administrado C++ y el código, la información de depuración se puede generar en archivos. pdb, [dependiendo de las opciones del](#BKMK_symbols_release) compilador que se usen. Crear archivos. pdb puede ser útil si posteriormente tiene que depurar la versión de lanzamiento.

Para más información sobre las configuraciones de compilación, vea [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md).

La configuración de compilación se puede modificar desde el menú **Compilar**, la barra de herramientas o las páginas de propiedades del proyecto. Las páginas de propiedades del proyecto son específicas de un lenguaje. El procedimiento que se indica a continuación muestra cómo cambiar la configuración de compilación desde el menú y la barra de herramientas. Para obtener más información sobre cómo cambiar la configuración de compilación en proyectos de distintos lenguajes, vea la sección [vea también](#see-also) más adelante.

## <a name="change-the-build-configuration"></a>Cambiar la configuración de compilación

Para cambiar la configuración de compilación, puede:

* En el menú compilar, seleccione **Configuration Manager**y, a continuación, seleccione Depurar o **liberar**.

o

* En la barra de herramientas, elija **Depurar** o **Versión** en el cuadro de lista **Configuraciones de soluciones**.

  ![configuración de compilación de barras de herramientas](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")

## <a name="BKMK_symbols_release"></a>Generar archivos de símbolos (. pdb) para una compilaciónC#( C++,, Visual Basic F#,)

Puede optar por generar archivos de símbolos (. pdb) y la información de depuración que se va a incluir. Para la mayoría de los tipos de proyecto, el compilador genera archivos de símbolos de forma predeterminada para las compilaciones de depuración y versión, mientras que otros valores predeterminados varían según el tipo de proyecto y la versión

> [!IMPORTANT]
> El depurador solo cargará un archivo .pdb de un archivo ejecutable que coincida exactamente con el archivo .pdb creado cuando se compiló el archivo ejecutable (es decir, el archivo .pdb debe ser el original o una copia del archivo .pdb original). Para obtener más información, vea [¿por qué Visual Studio requiere que los archivos de símbolos del depurador coincidan exactamente con los archivos binarios con los que se crearon?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

Cada tipo de proyecto puede tener una manera diferente de establecer estas opciones.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Generar archivos de símbolos para C#un proyecto de, ASP.NET o Visual Basic

Para obtener información detallada sobre la configuración del proyecto para C# las configuraciones de depuración en o Visual Basic, vea configuración del proyecto [para una C# ](../debugger/project-settings-for-csharp-debug-configurations.md) configuración de depuración o configuración del [proyecto para una configuración de](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)depuración de Visual Basic.

1. En el Explorador de soluciones, seleccione el proyecto.

2. Seleccione el icono de **propiedades** (o presione **Alt + entrar**).

3. En el panel lateral, elija compilar (o compilar en Visual Basic).

4. En la lista **configuración** , elija depurar o **liberar**.

5. Seleccione el botón **avanzadas** (o el botón **Opciones de compilación avanzadas** en Visual Basic).

6. En la **lista información** de depuración (o en la lista **generar** información de depuración en Visual Basic), elija **completo**, **solo PDB**o **portátil**.

   El formato portátil es el formato multiplataforma más reciente para .NET Core. Para obtener más información sobre las opciones, vea [cuadro de diálogo ConfiguraciónC#de compilación avanzada ()](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

   ![Generar archivos PDB para C# compilaciones en](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

7. Compilar el proyecto.

   El compilador crea los archivos de símbolos en la misma carpeta que el ejecutable o el archivo de salida principal.

### <a name="generate-symbol-files-for-a-c-project"></a>Generar archivos de símbolos para C++ un proyecto

1. En el Explorador de soluciones, seleccione el proyecto.

2. Seleccione el icono de **propiedades** (o presione **Alt + entrar**).

3. En la lista **configuración** , elija depurar o **liberar**.

4. En el panel lateral, elija **vinculador >** depurar y, a continuación, seleccione Opciones para **generar información**de depuración.

   Para obtener información detallada sobre la configuración del proyecto para C++las configuraciones de depuración en, vea [configuración del proyecto para una C++ configuración](../debugger/project-settings-for-a-cpp-debug-configuration.md)de depuración.

5. Configurar opciones para **generar archivos de base de datos de programa**.

   En la C++ mayoría de los proyectos, el `$(OutDir)$(TargetName).pdb`valor predeterminado es, que genera archivos. pdb en la carpeta de salida.

   ![Generar archivos PDB para C++ compilaciones en](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus")

6. Compilar el proyecto.

   El compilador crea los archivos de símbolos en la misma carpeta que el ejecutable o el archivo de salida principal.

## <a name="see-also"></a>Vea también

- [Especificar archivos de símbolos (. pdb) y archivos de código fuente en el depurador de Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)<br/>
- [Preparación y configuración del depurador](../debugger/debugger-settings-and-preparation.md)<br/>
- [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)<br/>
- [Configuración del proyecto para una configuración de depuración de C#](../debugger/project-settings-for-csharp-debug-configurations.md)<br/>
- [Configuración de proyectos para una configuración de depuración en Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)<br/>
- [Cómo: Crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md)
