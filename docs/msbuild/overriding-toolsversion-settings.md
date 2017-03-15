---
title: "Invalidar el valor de la versi&#243;n de herramientas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, compilar soluciones con"
  - "MSBuild, invalidar el valor de la versión de herramientas"
ms.assetid: ccd42c07-0fb6-4e8b-9ebb-a6a6db18aa2e
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Invalidar el valor de la versi&#243;n de herramientas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede cambiar el Conjunto de herramientas para los proyectos y soluciones en una de tres maneras:  
  
1.  utilizando el modificador `/ToolsVersion` \(o `/tv`, abreviado\) cuando compile el proyecto o solución desde la línea de comandos  
  
2.  estableciendo el parámetro `ToolsVersion` en la tarea MSBuild.  
  
3.  estableciendo la propiedad `$(ProjectToolsVersion)` en un proyecto dentro de una solución.  Esto permite compilar un proyecto en una solución con una versión del Conjunto de herramientas diferente de la de los otros proyectos.  
  
## Invalidar el valor de la versión de herramientas de los proyectos y soluciones en compilaciones de la línea de comandos  
 Aunque los proyectos de Visual Studio normalmente se compilan con la versión de herramientas especificada en el archivo de proyecto, puede utilizar el modificador `/ToolsVersion` \(o `/tv`\) en la línea de comandos invalidar ese valor y compilar todos los proyectos y sus dependencias entre proyectos con un conjunto de herramientas diferente.  Por ejemplo:  
  
```  
msbuild.exe someproj.proj /tv:12.0 /p:Configuration=Debug  
```  
  
 En este ejemplo, todos los proyectos se compilan con ToolsVersion 12.0. \(No obstante, vea la sección "Orden de prioridad" más adelante en este tema.\)  
  
 Cuando se utiliza el modificador `/tv` en la línea de comandos, también puede utilizar la propiedad `$(ProjectToolsVersion)` en proyectos individuales para compilarlos con un valor de versión de herramientas diferente de otros proyectos de la solución.  
  
## Invalidar el valor de la versión de herramientas mediante el parámetro ToolsVersion de la tarea MSBuild  
 La tarea MSBuild es el principal medio que tiene un proyecto para compilar otro.  Para que la tarea MSBuild compile un proyecto con una versión de herramientas diferente de la especificada en el proyecto, dispone de un parámetro de tarea opcional denominado `ToolsVersion`.  En el siguiente ejemplo se muestra cómo utilizar este parámetro:  
  
1.  Cree un archivo denominado `projectA.proj` y que contenga el código siguiente:  
  
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
  
2.  Cree otro archivo denominado `projectB.proj` y que contenga el código siguiente:  
  
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
  
3.  Escriba el comando siguiente en un símbolo del sistema:  
  
    ```  
    msbuild projectA.proj /t:go /toolsversion:3.5  
    ```  
  
4.  Aparece la salida siguiente.  Para `projectA`, el valor `/toolsversion:3.5` de la línea de comandos invalida el valor `ToolsVersion=12.0` de la etiqueta `Project`.  
  
     Una tarea llama a `ProjectB` en `projectA`.  Esa tarea tiene `ToolsVersion=2.0`, que reemplaza el resto de valores de `ToolsVersion` para `projectB`.  
  
    ```  
    Output:  
      projectA.proj  
      MSBuildToolsVersion: 3.5  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v3.5  
  
      projectB.proj  
      MSBuildToolsVersion: 2.0  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v2.0.50727  
    ```  
  
## Orden de prioridad  
 El orden de prioridad, de mayor a menor, utilizado para determinar la `ToolsVersion` es:  
  
1.  El atributo `ToolsVersion` de la tarea MSBuild utilizado para compilar el proyecto, si existe.  
  
2.  Modificador `/toolsversion` \(o `/tv`\) que se utiliza en el comando msbuild.exe, si lo hay.  
  
3.  Si se establece la variable de entorno `MSBUILDTREATALLTOOLSVERSIONSASCURRENT`, utilice `ToolsVersion` actual.  
  
4.  Si se establece la variable de entorno `MSBUILDTREATHIGHERTOOLSVERSIONASCURRENT` y `ToolsVersion` definido en el archivo de proyecto es mayor que `ToolsVersion` actual, utilice `ToolsVersion` actual.  
  
5.  Si se establece la variable de entorno `MSBUILDLEGACYDEFAULTTOOLSVERSION` o si `ToolsVersion` no se establece, se utilizan los siguientes pasos:  
  
    1.  El atributo `ToolsVersion` del elemento [Project](../msbuild/project-element-msbuild.md) del archivo de proyecto.  Si no existe este atributo, se supone que es la versión actual.  
  
    2.  La versión de herramientas predeterminada del archivo MSBuild.exe.config.  
  
    3.  Las versión de herramientas predeterminada del Registro.  Para obtener más información, vea [Configuraciones de conjuntos de herramientas estándar y personalizados](../msbuild/standard-and-custom-toolset-configurations.md).  
  
6.  Si la variable de entorno `MSBUILDLEGACYDEFAULTTOOLSVERSION` no se establece, se utilizan los siguientes pasos:  
  
    1.  Si la variable de entorno `MSBUILDDEFAULTTOOLSVERSION` se establece en `ToolsVersion` que existe, utilícela.  
  
    2.  Si `DefaultOverrideToolsVersion` se establece en MSBuild.exe.config, utilícelo.  
  
    3.  Si `DefaultOverrideToolsVersion` se establece en en el Registro, úselo.  
  
    4.  De lo contrario, use el `ToolsVersion` actual.  
  
## Vea también  
 [Compatibilidad con múltiples versiones \(multi\-targeting\)](../msbuild/msbuild-multitargeting-overview.md)   
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)   
 [Conjunto de herramientas \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md)   
 [Configuraciones de conjuntos de herramientas estándar y personalizados](../msbuild/standard-and-custom-toolset-configurations.md)