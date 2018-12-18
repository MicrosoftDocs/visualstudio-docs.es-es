---
title: Uso de varios procesadores para compilar proyectos | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67b873b8ab1668ea2fea3b3bf0487339a86c9ffe
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49199919"
---
# <a name="using-multiple-processors-to-build-projects"></a>Uso de varios procesadores para compilar proyectos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
MSBuild puede aprovechar las ventajas de los sistemas que tienen varios procesadores o varios núcleos. Se crea un proceso de compilación independiente para cada procesador disponible. Por ejemplo, si el sistema tiene cuatro procesadores, se crean cuatro procesos de compilación. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] puede procesar estas compilaciones simultáneamente y, por tanto, el tiempo de compilación se reduce. Sin embargo, la compilación en paralelo presenta algunos cambios en la forma en la que tienen lugar los procesos de compilación. En este tema se analizan estos cambios.  
  
## <a name="project-to-project-references"></a>Referencias entre proyectos  
 Cuando [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] encuentra una referencia entre proyectos mientras está utilizando compilaciones en paralelo para compilar un proyecto, solo compila la referencia una vez. Si dos proyectos tienen la misma referencia entre proyectos, la referencia no se recompila para cada proyecto. En su lugar, el motor de compilación devuelve la misma referencia entre proyectos a los dos proyectos que dependen de él. En la misma referencia entre proyectos se proporcionan las solicitudes futuras para el mismo destino en la sesión.  
  
## <a name="cycle-detection"></a>Detección de ciclos  
 La detección de ciclos funciona igual que en [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 2.0, solo que ahora [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] puede notificar la detección del ciclo en un momento diferente o en la compilación.  
  
## <a name="errors-and-exceptions-during-parallel-builds"></a>Errores y excepciones durante las compilaciones en paralelo  
 En las compilaciones en paralelo, los errores y excepciones pueden producirse en momentos diferentes que en una compilación no paralela, y cuando un proyecto no se compila, las demás compilaciones de proyectos continúan. Si se producen errores en un proyecto, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] no detendrá la compilación de proyectos que se está ejecutando en paralelo. Los demás proyectos seguirán compilándose hasta que terminen correctamente o con errores. Sin embargo, si se ha habilitado <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A>, no se detendrá ninguna compilación aunque se produzca un error.  
  
## <a name="visual-c-project-vcproj-and-solution-sln-files"></a>Archivos de proyecto (.vcproj) y solución (.sln) de Visual C++  
 Los archivos de proyecto (.vcproj) y los archivos de solución (.sln) de [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] se pueden pasar a [MSBuild Task](../msbuild/msbuild-task.md). Para los proyectos de [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], se llama a VCWrapperProject y, a continuación, se crea el proyecto de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] interno. Para las soluciones de [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], se crea un SolutionWrapperProject y, a continuación, se crea el proyecto de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] interno. En ambos casos, el proyecto resultante se trata igual que cualquier otro proyecto de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
## <a name="multi-process-execution"></a>Ejecución con varios procesos  
 Casi todas las actividades relacionadas con la compilación requieren que el directorio actual permanezca constante a lo largo del proceso de compilación para evitar errores relacionados con la ruta de acceso. Por consiguiente, los proyectos no se pueden ejecutar en subprocesos diferentes de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] porque haría que se crearan varios directorios.  
  
 Para evitar este problema y habilitar al mismo tiempo las compilaciones para varios procesadores, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] utiliza el "aislamiento de procesos". Mediante el aislamiento de procesos, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pueden crear un máximo de `n` procesos, donde `n` es el número de procesadores disponibles en el sistema. Por ejemplo, si [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] compila una solución en un sistema que tiene dos procesadores de impresión, sólo se crean dos procesos de compilación. Estos procesos se reutilizan para compilar todos los proyectos de la solución.  
  
## <a name="see-also"></a>Vea también  
 [Compilar varios proyectos en paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)   
 [Tareas](../msbuild/msbuild-tasks.md)



