---
title: Uso de varios procesadores para compilar proyectos | Microsoft Docs
description: Obtenga información sobre cómo MSBuild aprovecha los sistemas que tienen varios procesadores o núcleos mediante la creación de un proceso de compilación independiente para cada procesador disponible.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c1560b40fe94af8dae5223981dd8e0c790320085
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946376"
---
# <a name="use-multiple-processors-to-build-projects"></a>Uso de varios procesadores para compilar proyectos

MSBuild puede aprovechar las ventajas de los sistemas que tienen varios procesadores o varios núcleos. Se crea un proceso de compilación independiente para cada procesador disponible. Por ejemplo, si el sistema tiene cuatro procesadores, se crean cuatro procesos de compilación. MSBuild puede procesar estas compilaciones simultáneamente y, por tanto, el tiempo de compilación se reduce. Sin embargo, la compilación en paralelo presenta algunos cambios en la forma en la que tienen lugar los procesos de compilación. En este tema se analizan estos cambios.

## <a name="project-to-project-references"></a>Referencias entre proyectos

 Cuando Microsoft Build Engine encuentra una referencia entre proyectos (P2P) mientras está utilizando compilaciones en paralelo para compilar un proyecto, solo compila la referencia una vez. Si dos proyectos tienen la misma referencia entre proyectos, la referencia no se recompila para cada proyecto. En su lugar, el motor de compilación devuelve la misma referencia entre proyectos a los dos proyectos que dependen de él. En la misma referencia entre proyectos se proporcionan las solicitudes futuras para el mismo destino en la sesión.

## <a name="cycle-detection"></a>Detección de ciclos

 La detección de ciclos funciona igual que en MSBuild 2.0, solo que ahora MSBuild puede notificar la detección del ciclo en un momento diferente o en la compilación.

## <a name="errors-and-exceptions-during-parallel-builds"></a>Errores y excepciones durante las compilaciones en paralelo

 En las compilaciones en paralelo, los errores y excepciones pueden producirse en momentos diferentes que en una compilación no paralela, y cuando un proyecto no se compila, las demás compilaciones de proyectos continúan. Si se producen errores en un proyecto, MSBuild no detendrá la compilación de proyectos que se está ejecutando en paralelo. Los demás proyectos seguirán compilándose hasta que terminen correctamente o con errores. Sin embargo, si se ha habilitado <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A>, no se detendrá ninguna compilación aunque se produzca un error.

## <a name="c-project-vcxproj-and-solution-sln-files"></a>Archivos de proyecto (.vcxproj) y solución (.sln) de C++

 Los archivos de proyecto ( *.vcxproj*) y los archivos de solución ( *.sln*) de C++ se pueden pasar a la [tarea de MSBuild](../msbuild/msbuild-task.md). Para los proyectos de C++, se llama a VCWrapperProject y, a continuación, se crea el proyecto de MSBuild interno. Para las soluciones de C++, se crea un elemento SolutionWrapperProject y, a continuación, se crea el proyecto de MSBuild interno. En ambos casos, el proyecto resultante se trata igual que cualquier otro proyecto de MSBuild.

## <a name="multi-process-execution"></a>Ejecución con varios procesos

 Casi todas las actividades relacionadas con la compilación requieren que el directorio actual permanezca constante a lo largo del proceso de compilación para evitar errores relacionados con la ruta de acceso. Por consiguiente, los proyectos no se pueden ejecutar en subprocesos diferentes de MSBuild porque haría que se crearan varios directorios.

 Para evitar este problema y habilitar al mismo tiempo las compilaciones para varios procesadores, MSBuild utiliza el "aislamiento de procesos". Mediante el aislamiento de procesos, MSBuild puede crear un máximo de `n` procesos, donde `n` es el número de procesadores disponibles en el sistema. Por ejemplo, si MSBuild compila una solución en un sistema que tiene dos procesadores de impresión, solo se crean dos procesos de compilación. Estos procesos se reutilizan para compilar todos los proyectos de la solución.

## <a name="see-also"></a>Consulte también

- [Compilar varios proyectos en paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
- [Tareas](../msbuild/msbuild-tasks.md)
