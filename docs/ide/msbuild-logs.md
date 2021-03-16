---
title: Solución de problemas y creación de registros para MSBuild
description: Aprenda a diagnosticar problemas de compilación en el proyecto de Visual Studio y, en caso necesario, a crear un registro para enviarlo a Microsoft para su investigación.
ms.custom: SEO-VS-2020
ms.date: 02/08/2021
ms.technology: vs-ide-compile
ms.topic: troubleshooting
helpviewer_keywords:
- msbuild logs"
author: corob-msft
ms.author: corob
manager: jmartens
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Generate build logs for msbuild projects to collect helpful information when troubleshooting issues.
ms.openlocfilehash: 3496eb5a0e8f699a994037ccc853a76e4f93e4ee
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225226"
---
# <a name="troubleshoot-and-create-logs-for-msbuild-problems"></a>Solución de problemas y creación de registros para MSBuild

Los procedimientos siguientes pueden ayudarle a diagnosticar problemas de compilación en su proyecto de Visual Studio y, si fuera necesario, crear un registro para enviarlo a Microsoft para su investigación.

## <a name="a-property-value-is-ignored"></a>Se omite un valor de propiedad

Si la propiedad de un proyecto aparece establecida en un valor determinado, pero no surte efecto en la compilación, siga estos pasos:

1. Abra el símbolo del sistema para desarrolladores de Visual Studio que corresponda a su versión de Visual Studio.
1. Ejecute el comando siguiente, después de sustituir los valores para la ruta de la solución, la configuración y el nombre del proyecto:

    ```cmd
    msbuild /p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /pp:out.xml MyProject.vcxproj
    ```

    Este comando genera un archivo de proyecto de msbuild "preprocesado" (out.xml). Puede buscar en ese archivo una propiedad específica para ver dónde está definido.

La última definición de una propiedad es lo que consume la compilación. Si la propiedad se establece dos veces, el segundo valor sobrescribe el primero. Además, MSBuild evalúa el proyecto en varias fases:

- PropertyGroups e Imports
- ItemDefinitionGroups
- ItemGroups
- Destinos

Por lo tanto, dado el orden siguiente:

```xml
<PropertyGroup>
   <MyProperty>A</MyProperty>
</PropertyGroup>
<ItemGroup>
   <MyItems Include="MyFile.txt"/>
</ItemGroup>
<ItemDefinitionGroup>
  <MyItems>
      <MyMetadata>$(MyProperty)</MyMetadata>
  </MyItems>
</ItemDefinitionGroup>
<PropertyGroup>
   <MyProperty>B</MyProperty>
</PropertyGroup>
```

El valor de "MyMetadata" para el elemento "MyFile.txt" se evaluará en "B" durante la compilación (no "A" ni vacío)

## <a name="incremental-build-is-building-more-than-it-should"></a>La compilación incremental está compilando más de lo que debería

Si MSBuild está volviendo a compilar innecesariamente un proyecto o un elemento de proyecto, cree un registro de compilación detallado o binario. Puede buscar en el registro el archivo que se creó o compiló innecesariamente. La salida tendrá un aspecto similar a este:

```output
  Task "CL"

  Using cached input dependency table built from:

  F:\test\Project1\Project1\Debug\Project1.tlog\CL.read.1.tlog

  Outputs for F:\TEST\PROJECT1\PROJECT1\PROJECT1.CPP:
  F:\TEST\PROJECT1\PROJECT1\DEBUG\PROJECT1.OBJ
  Project1.cpp will be compiled because F:\TEST\PROJECT1\PROJECT1\PROJECT1.H was modified at 6/5/2019 12:37:09 PM.

  Outputs for F:\TEST\PROJECT1\PROJECT1\PROJECT1.CPP:
  F:\TEST\PROJECT1\PROJECT1\DEBUG\PROJECT1.OBJ

  Write Tracking Logs:
  Debug\Project1.tlog\CL.write.1.tlog
```

Si va a compilar en el IDE de Visual Studio (con información detallada sobre la ventana de salida), la **Ventana de salida** muestra el motivo por el cual cada proyecto no está actualizado:

```output
1>------ Up-To-Date check: Project: Project1, Configuration: Debug Win32 ------

1>Project is not up-to-date: build input 'f:\test\project1\project1\project1.h' was modified after the last build finished.
```

## <a name="create-a-binary-msbuild-log-at-the-command-prompt"></a>Creación de un registro de MSBuild binario en el símbolo del sistema

1. Abra el símbolo del sistema para desarrolladores de su versión de Visual Studio.

1. En el símbolo del sistema, ejecute uno de los comandos siguientes (no olvide usar los valores reales del proyecto y la configuración):

   ```cmd
   Msbuild /p:Configuration="MyConfiguration";Platform="x86" /bl MySolution.sln
   ```

   o

   ```cmd
   Msbuild /p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /bl MyProject.vcxproj
   ```

Se obtiene un archivo *msbuild.binlog* en el directorio desde el que ejecutó MSBuild.

## <a name="create-a-binary-msbuild-log-by-using-the-project-system-tools-extension"></a>Creación de un registro de MSBuild binario mediante la extensión de herramientas del sistema del proyecto

1. Descargue e instale la [extensión de herramientas del sistema del proyecto](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ProjectSystemTools).

1. Una vez instalada la extensión, algunos elementos nuevos aparecen en el menú **Ver** > **Otras ventanas**.

   ![Menú Otras ventanas](../ide/media/view-menu.png)

1. Seleccione **Ver** > **Otras ventanas** > **Build Logging** (Registro de compilación) para mostrar la ventana **Registro de compilación** en Visual Studio. Elija el primer icono de la barra de herramientas para iniciar la grabación de compilaciones normales y en tiempo de diseño en el sistema del proyecto.

   ![Ventana Registro de compilación](../ide/media/build-logging-click-to-record.png)

1. Una vez que se registra una compilación, aparece en la ventana Registro de compilación. Haga clic con el botón derecho en el elemento y seleccione **Guardar registros** en el menú contextual para guardar el archivo *.binlog*.

   ![Menú contextual Registro de compilación](../ide/media/build-logging-context-menu.png)

Puede verlo y buscar los archivos *.binlog* por medio del [visor de registros estructurado de Msbuild](http://www.msbuildlog.com/).

## <a name="create-a-detailed-log"></a>Creación de un registro detallado

1. En el menú principal de Visual Studio, vaya a **Herramientas** > **Opciones** > **Proyectos y soluciones** >**Compilar y ejecutar**.
1. Establezca el **nivel de detalle de la compilación del proyecto de Msbuild** en **Detallado** en los dos cuadros combinados. El primero controla el nivel de detalle de la compilación en la **Ventana de salida**, mientras que el segundo controla el nivel de detalle de la compilación en el archivo \<projectname\>.log que se crea en el directorio intermedio de cada proyecto durante la compilación.
2. Desde un símbolo del sistema para desarrolladores de Visual Studio, escriba uno de estos comandos, sustituyendo sus valores reales de ruta de acceso y configuración:

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /fl MySolution.sln
    ```

    o

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /fl MyProject.vcxproj
    ```

    Se creará un archivo Msbuild.log en el directorio desde el que ejecutó msbuild.

## <a name="see-also"></a>Consulte también

- [Solucionar problemas de Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
