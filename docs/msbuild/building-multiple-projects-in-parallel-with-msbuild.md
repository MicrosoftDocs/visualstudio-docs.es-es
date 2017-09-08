---
title: "Compilación de varios proyectos en paralelo con MSBuild | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parallel project builds
- building multiple projects in parallel
- msbuild, building projects in parallel
ms.assetid: c8c9aadc-33ad-4aa1-b07d-b879e9eabda0
caps.latest.revision: 20
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 17defdd0b96ec1c3273fc6b845af844b031a4a17
ms.openlocfilehash: 6aa02abdbfe8ea55b6e3434dbc859b5fa5d6a5e3
ms.contentlocale: es-es
ms.lasthandoff: 09/06/2017

---
# <a name="building-multiple-projects-in-parallel-with-msbuild"></a>Compilar varios proyectos en paralelo con MSBuild
Puede usar MSBuild para compilar varios proyectos más rápidamente si los ejecuta en paralelo. Para ejecutar compilaciones en paralelo, use los parámetros siguientes en un equipo con varios procesadores o varios núcleos:  
  
-   El modificador `/maxcpucount` en un símbolo del sistema.  
  
-   El parámetro de tarea <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A> en una tarea de MSBuild.  
  
> [!NOTE]
>  El modificador **/verbosity** (**/v**) en una línea de comandos también puede afectar al rendimiento de la compilación. Es posible que disminuya el rendimiento de la compilación si el nivel de detalle de la información del registro de compilación se establece en "detailed" o "diagnostic", que se usan para solucionar problemas. Para obtener más información, consulte [Obtener registros de compilación](../msbuild/obtaining-build-logs-with-msbuild.md) y [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="maxcpucount-switch"></a>Modificador /maxcpucount  
 Si utiliza el modificador `/maxcpucount`, o `/m` abreviado, MSBuild puede crear el número especificado de procesos de MSBuild.exe que se pueden ejecutar en paralelo. Estos procesos también se denominan "procesos de trabajo". Cada proceso de trabajo utiliza un núcleo o procesador independiente, si hay alguno disponible, para compilar un proyecto al mismo tiempo ya que los demás procesadores disponibles pueden estar compilando otros proyectos. Por ejemplo, si se establece este modificador en un valor "4", MSBuild creará cuatro procesos de trabajo para compilar el proyecto.  
  
 Si incluye el modificador `/maxcpucount` sin especificar un valor, MSBuild podrá usar todos los procesadores de que disponga el equipo.  
  
 Para obtener más información sobre este modificador, que se introdujo en MSBuild 3.5, vea [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md).  
  
 En el ejemplo siguiente se indica a MSBuild que use tres procesos de trabajo. Si utiliza esta configuración, MSBuild puede compilar tres proyectos al mismo tiempo.  
  
```  
msbuild.exe myproj.proj /maxcpucount:3  
```  
  
## <a name="buildinparallel-task-parameter"></a>Parámetro de tarea BuildInParallel  
 `BuildInParallel` es un parámetro booleano opcional de una tarea de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Cuando `BuildInParallel` se establece en `true` (su valor predeterminado es `false`), se generan varios procesos de trabajo para compilar al mismo tiempo el mayor número de proyectos posible. Para que funcione correctamente, el modificador `/maxcpucount` debe establecerse en un valor mayor que 1 y el sistema debe tener al menos dos núcleos o dos o más procesadores.  
  
 A continuación, se muestra un ejemplo tomado de microsoft.common.targets, sobre cómo establecer el parámetro `BuildInParallel`.  
  
```  
<PropertyGroup>  
    <BuildInParallel Condition="'$(BuildInParallel)' ==   
        ''">true</BuildInParallel>  
</PropertyGroup>  
<MSBuild  
    Projects="@(_MSBuildProjectReferenceExistent)"  
    Targets="GetTargetPath"  
    BuildInParallel="$(BuildInParallel)"  
    Properties="%(_MSBuildProjectReferenceExistent.SetConfiguration);   
        %(_MSBuildProjectReferenceExistent.SetPlatform)"  
    Condition="'@(NonVCProjectReference)'!='' and   
        ('$(BuildingSolutionFile)' == 'true' or   
        '$(BuildingInsideVisualStudio)' == 'true' or   
        '$(BuildProjectReferences)' != 'true') and     
        '@(_MSBuildProjectReferenceExistent)' != ''"  
    ContinueOnError="!$(BuildingProject)">  
    <Output TaskParameter="TargetOutputs"   
        ItemName="_ResolvedProjectReferencePaths"/>  
</MSBuild>  
```  
  
## <a name="see-also"></a>Vea también  
 [Uso de varios procesadores para compilar proyectos](../msbuild/using-multiple-processors-to-build-projects.md)   
 [Escribir registradores que reconocen varios procesadores](../msbuild/writing-multi-processor-aware-loggers.md)   
 [Blog sobre la optimización del paralelismo de compilación de C++](http://go.microsoft.com/fwlink/?LinkId=251457)

