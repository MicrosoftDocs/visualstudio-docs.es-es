---
title: Solución de problemas y creación de registros para MSBuild
ms.date: 06/27/2019
ms.topic: conceptual
helpviewer_keywords:
- msbuild logs"
author: mikeblome
ms.author: mblome
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Generate build logs for msbuild projects to collect helpful information when troubleshooting issues.
ms.openlocfilehash: c3db56ac7ea60ce88beae6698c974ac91373ed00
ms.sourcegitcommit: 6f7a740750b2cd17ea2275c3d046caebc9782917
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2019
ms.locfileid: "67518201"
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

Si MSBuild está volviendo a compilar innecesariamente un proyecto o un elemento de proyecto, cree un registro de compilación detallado o binario. Puede buscar en el registro el archivo que se ha creado o compilado innecesariamente. La salida tendrá un aspecto similar a este:

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

## <a name="create-a-binary-msbuild-log"></a>Creación de un registro de msbuild binario

1. Abra el símbolo del sistema para desarrolladores de su versión de Visual Studio.
1. En el símbolo del sistema, ejecute uno de los comandos siguientes (no olvide usar los valores reales del proyecto y la configuración):

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /bl MySolution.sln
    ```

    o

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /bl MyProject.vcxproj
    ```

Se creará un archivo Msbuild.binlog en el directorio desde el que ejecutó MSBuild. Puede verlo y buscar en él por medio del [visor de registros estructurado de Msbuild](http://www.msbuildlog.com/).

## <a name="create-a-detailed-log"></a>Creación de un registro detallado

1. En el menú principal de Visual Studio, vaya a **Herramientas** > **Opciones** > **Proyectos y soluciones** >**Compilar y ejecutar**.
1. Establezca el **nivel de detalle de la compilación del proyecto de Msbuild** en **Detallado** en los dos cuadros combinados. El primero controla el nivel de detalle de la compilación en la **Ventana de salida** y el segundo controla el nivel de detalle de la compilación en el archivo \<nombreproyecto\>.log que se crea en el directorio intermedio de cada proyecto durante la compilación.
1. Desde un símbolo del sistema para desarrolladores de Visual Studio, escriba uno de estos comandos, sustituyendo sus valores reales de ruta de acceso y configuración:

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /fl MySolution.sln 
    ```

    o

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /fl MyProject.vcxproj
    ```

    Se creará un archivo Msbuild.log en el directorio desde el que ejecutó msbuild.
