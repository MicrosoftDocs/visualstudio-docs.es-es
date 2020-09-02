---
title: Invalidar la configuración de ToolsVersion | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding ToolsVersion setting
- MSBuild, building solutions with
ms.assetid: ccd42c07-0fb6-4e8b-9ebb-a6a6db18aa2e
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 468561a627a3ad7eb477328b5afef794c7acf2c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199945"
---
# <a name="overriding-toolsversion-settings"></a>Invalidar el valor de la versión de herramientas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede cambiar el conjunto de herramientas para los proyectos y soluciones de tres maneras:  
  
1. con el modificador `/ToolsVersion` (o `/tv`, para abreviar) cuando compile el proyecto o la solución desde la línea de comandos  
  
2. estableciendo el parámetro `ToolsVersion` en la tarea de MSBuild  
  
3. estableciendo la propiedad `$(ProjectToolsVersion)` en un proyecto de una solución. Esto le permite compilar un proyecto en una solución con una versión del conjunto de herramientas que difiere de la de otros proyectos.  
  
## <a name="override-the-toolsversion-settings-of-projects-and-solutions-on-command-line-builds"></a>Invalidar la configuración de ToolsVersion de proyectos y soluciones en compilaciones de la línea de comandos  
 Aunque normalmente los proyectos de Visual Studio creados con ToolsVersion se especifican en el archivo del proyecto, puede usar el modificador `/ToolsVersion` (o `/tv`) en la línea de comandos para invalidar ese valor y compilar todos los proyectos y sus dependencias proyecto a proyecto con un conjunto de herramientas diferente. Por ejemplo:  
  
```  
msbuild.exe someproj.proj /tv:12.0 /p:Configuration=Debug  
```  
  
 En este ejemplo, todos los proyectos se compilan con ToolsVersion 12.0. (En cambio, vea la sección "Orden de preferencia" posteriormente en este tema).  
  
 Al usar el modificador `/tv` en la línea de comandos, puede usar opcionalmente la propiedad `$(ProjectToolsVersion)` en proyectos individuales para compilarlos con un valor de ToolsVersion diferente que el de los demás proyectos de la solución.  
  
## <a name="override-the-toolsversion-settings-using-the-toolsversion-parameter-of-the-msbuild-task"></a>Invalidar la configuración de ToolsVersion con el parámetro ToolsVersion de la tarea de MSBuild  
 La tarea de MSBuild es el medio principal para que un proyecto compile otro. Para permitir que la tarea de MSBuild compile un proyecto con un ToolsVersion diferente que el especificado en el proyecto, proporciona un parámetro de tarea opcional denominado `ToolsVersion`. En el siguiente ejemplo se muestra cómo se usa este parámetro:  
  
1. Cree un archivo denominado `projectA.proj` y que incluya el siguiente código:  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
    ToolsVersion="12.0">  
  
        <Target Name="go" >   
            <Message Text="projectA.proj" />  
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />  
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />  
  
            <MSBuild Projects="projectB.proj"  
                ToolsVersion="2.0"  
                Targets="go" />  
        </Target>  
    </Project>  
    ```  
  
2. Cree otro archivo denominado `projectB.proj` y que incluya el siguiente código:  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
    ToolsVersion="12.0">  
  
        <Target Name="go">  
            <Message Text="projectB.proj" />  
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />  
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />  
        </Target>  
    </Project>  
    ```  
  
3. En un símbolo del sistema, escriba el siguiente comando:  
  
    ```  
    msbuild projectA.proj /t:go /toolsversion:3.5  
    ```  
  
4. Aparece el siguiente resultado. Para `projectA`, la configuración de `/toolsversion:3.5` en la línea de comandos invalida la configuración de `ToolsVersion=12.0` en la etiqueta `Project`.  
  
     Una tarea llama a `ProjectB` en `projectA`. Esa tarea tiene `ToolsVersion=2.0`, que invalida las otras configuraciones de `ToolsVersion` para `projectB`.  
  
    ```  
    Output:  
      projectA.proj  
      MSBuildToolsVersion: 3.5  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v3.5  
  
      projectB.proj  
      MSBuildToolsVersion: 2.0  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v2.0.50727  
    ```  
  
## <a name="order-of-precedence"></a>Orden de precedencia  
 El orden de prioridad, del más alto al más bajo, que se usa para determinar `ToolsVersion` es:  
  
1. El atributo `ToolsVersion` en la tarea de MSBuild que se usa para compilar el proyecto, si existe.  
  
2. El modificador `/toolsversion` (o `/tv`) que se usa en el comando msbuild.exe, si existe.  
  
3. Si se establece la variable de entorno `MSBUILDTREATALLTOOLSVERSIONSASCURRENT`, después use el `ToolsVersion` actual.  
  
4. Si se establece la variable de entorno `MSBUILDTREATHIGHERTOOLSVERSIONASCURRENT` y el `ToolsVersion` definido en el archivo del proyecto es mayor que el `ToolsVersion` actual, use el `ToolsVersion` actual.  
  
5. Si se establece la variable de entorno `MSBUILDLEGACYDEFAULTTOOLSVERSION`, o si `ToolsVersion` no se establece, entonces se usan los pasos siguientes:  
  
    1. El atributo `ToolsVersion` del elemento [Project](../msbuild/project-element-msbuild.md) del archivo del proyecto. Si el atributo no existe, se presupone que es la versión actual.  
  
    2. La versión de las herramientas predeterminada en el archivo MSBuild.exe.config.  
  
    3. La versión de las herramientas predeterminada en el registro. Para obtener más información, vea [configuraciones de conjuntos de herramientas estándar y personalizados](../msbuild/standard-and-custom-toolset-configurations.md).  
  
6. Si no se establece la variable de entorno `MSBUILDLEGACYDEFAULTTOOLSVERSION`, entonces se usan los pasos siguientes:  
  
    1. Si se establece la variable de entorno `MSBUILDDEFAULTTOOLSVERSION` en un `ToolsVersion` que existe, úselo.  
  
    2. Si `DefaultOverrideToolsVersion` se establece en MSBuild.exe.config, úselo.  
  
    3. Si `DefaultOverrideToolsVersion` se establece en el registro, úselo.  
  
    4. De otro modo, use el `ToolsVersion` actual.  
  
## <a name="see-also"></a>Consulte también  
 [Multitargeting](../msbuild/msbuild-multitargeting-overview.md)   
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)   
 [Conjunto de herramientas (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)   
 [Configuraciones de conjuntos de herramientas estándar y personalizados](../msbuild/standard-and-custom-toolset-configurations.md)
