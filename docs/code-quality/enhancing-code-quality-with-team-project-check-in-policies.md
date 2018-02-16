---
title: "Mejorar la calidad del código con directivas de protección del proyecto de equipo | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code quality, using check-in policies
- team-based development, enhancing code quality
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c82bc929fa7633719c06569cb3dded5df651a349
ms.sourcegitcommit: e5bd950df79175a96fe62b3d4b17a3ef536ec4c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2018
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>Mejorar la calidad del código con directivas de protección de equipo

Cuando se usa el Control de versiones de Team Foundation (TFVC), puede crear directivas de protección para los proyectos de equipo. Aplicación de prácticas que permitan obtener un código mejor y un desarrollo del grupo más eficaz. Las directivas de protección son reglas que se establecen en el nivel del proyecto de equipo y cuya implantación es obligatoria en los equipos de los desarrolladores antes de que el código pueda protegerse.

Puede especificar las siguientes directivas de protección del proyecto de equipo:

- **Compilaciones**: requiere que las interrupciones de compilación creadas durante una compilación se corrijan antes de una nueva protección.

- **Comentarios del conjunto de cambios**: requiere que los usuarios proporcionen comentarios al proteger los cambios.

- **Análisis de código**: requiere la ejecución del análisis de código antes de llevar a cabo la protección.

- **Elementos de trabajo**: requiere que uno o varios elementos de trabajo estén asociados a la protección.

> [!IMPORTANT]
> Para utilizar las directivas de protección, se debe conectar a [!INCLUDE[vststfsLong](../code-quality/includes/vststfslong_md.md)].

## <a name="common-tasks"></a>Tareas comunes

|Tarea|Contenido adicional|
|----------|------------------------|
|**Crear y usar directivas de protección de análisis de código:** puede elegir un conjunto estándar de reglas de análisis de código o crear un conjunto personalizado.|[Crear y usar directivas de protección del análisis de código](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|

## <a name="related-tasks"></a>Tareas relacionadas

|Tarea|Contenido adicional|
|----------|------------------------|
|**Usar análisis de código en el proceso de desarrollo:** los miembros del equipo ejecutan análisis de código en sus equipos de desarrollo. En Visual Studio, los desarrolladores configuran y ejecutan series de análisis de código en proyectos de código concretos, ven y analizan los problemas que surgen en las ejecuciones y crean elementos de trabajo para las advertencias.|[Analizar la calidad de la aplicación](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|
|**Crear y ejecutar pruebas unitarias:** las pruebas unitarias proporcionan a los desarrolladores y evaluadores una forma rápida de buscar errores lógicos en los métodos de clases en proyectos de C#, Visual Basic y C++. Una prueba unitaria se puede crear una vez y ejecutarse cada vez que se cambia el código fuente, a fin de asegurarse de que no se incluye ningún error.|[Haga una prueba unitaria de su código](../test/unit-test-your-code.md)|
|**Seguimiento de elementos de trabajo y defectos:** puede usar elementos de trabajo para llevar a cabo el seguimiento y la administración del trabajo y la información del proyecto de equipo. Un elemento de trabajo es un registro de base de datos que [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] usa para seguir la asignación y el progreso del trabajo. Se pueden usar diferentes tipos de elementos de trabajo para seguir diversos tipos de trabajo, como requisitos del cliente, errores del producto y tareas de desarrollo.|[Elementos de trabajo (VSTS)](/vsts/work/work-items/index)|

## <a name="external-resources"></a>Recursos externos

[Pruebas de entrega continua con Visual Studio 2012. Capítulo 2: Pruebas unitarias: Prueba del interior](http://go.microsoft.com/fwlink/?LinkID=255188)