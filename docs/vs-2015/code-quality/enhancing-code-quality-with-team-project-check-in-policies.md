---
title: Mejorar la calidad del código con directivas de protección del proyecto de equipo | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code quality, using check-in policies
- team-based development, enhancing code quality
ms.assetid: 0ab72c33-148a-4a8a-a7bf-046995514c84
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c7b95155db18e9aa879b11cadf21b33cb0189ff9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60103373"
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>Mejorar la calidad del código con directivas de protección de equipo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando se usa el Control de versiones de Team Foundation (TFVC), puede crear directivas de protección para los proyectos de equipo. Aplicación de prácticas que permitan obtener un código mejor y un desarrollo del grupo más eficaz. Las directivas de protección son reglas que se establecen en el nivel del proyecto de equipo y cuya implantación es obligatoria en los equipos de los desarrolladores antes de que el código pueda protegerse.  
  
 Puede especificar las siguientes directivas de protección del proyecto de equipo:  
  
- **Compilaciones**: Requiere que las interrupciones de compilación creadas durante una compilación se corrijan antes de una nueva protección.  
  
- **Comentarios del conjunto de cambios**: Requiere que los usuarios proporcionen comentarios al proteger los cambios.  
  
- **Análisis de código**: Requiere la ejecución del análisis de código antes de protegerlo.  
  
- **Los elementos de trabajo**: Requiere que uno o varios elementos de trabajo estén asociados a la comprobación.  
  
> [!IMPORTANT]
>  Para utilizar las directivas de protección, se debe conectar a [!INCLUDE[vststfsLong](../includes/vststfslong-md.md)].  
  
## <a name="common-tasks"></a>Tareas comunes  
  
|Tarea|Contenido adicional|  
|----------|------------------------|  
|**Crear y usar directivas de protección:** Crear directivas de protección mediante el uso de la configuración del proyecto de equipo de [!INCLUDE[esprscc](../includes/esprscc-md.md)].|[Establecer y aplicar pruebas de calidad](http://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|  
|**Crear y usar directivas de protección de análisis de código:** Puede elegir un conjunto estándar de reglas de análisis de código, o puede crear un conjunto personalizado.|[Crear y usar directivas de protección del análisis de código](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|  
  
## <a name="related-tasks"></a>Tareas relacionadas  
  
|Tarea|Contenido adicional|  
|----------|------------------------|  
|**Configurar el entorno de desarrollo:** Antes de crear o modificar el código, debe configurar el desarrollo y entornos de prueba utilizando el código fuente adecuado. Si trabaja con bases de datos, debe tener acceso a su representación sin conexión.|[Configuración de entornos de desarrollo](http://msdn.microsoft.com/7b686610-d379-4ca0-9608-73ef0e576e3a)|  
|**Use el análisis de código en proceso de desarrollo:** Los miembros del equipo ejecutan análisis de código en sus equipos de desarrollo. En Visual Studio, los desarrolladores configuran y ejecutan series de análisis de código en proyectos de código concretos, ven y analizan los problemas que surgen en las ejecuciones y crean elementos de trabajo para las advertencias.|[Analizar la calidad de la aplicación](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|  
|**Crear y ejecutar pruebas unitarias:** Las pruebas unitarias proporcionan a los desarrolladores y evaluadores una forma rápida de buscar errores lógicos en los métodos de clases en proyectos de C#, Visual Basic .NET y C++. Una prueba unitaria se puede crear una vez y ejecutarse cada vez que se cambia el código fuente, a fin de asegurarse de que no se incluye ningún error.|[Haga una prueba unitaria de su código](../test/unit-test-your-code.md)|  
|**Seguimiento de elementos de trabajo y defectos:** Puede usar los elementos de trabajo para realizar un seguimiento y administrar su trabajo y la información sobre el proyecto de equipo. Un elemento de trabajo es un registro de base de datos que [!INCLUDE[esprfound](../includes/esprfound-md.md)] usa para seguir la asignación y el progreso del trabajo. Se pueden usar diferentes tipos de elementos de trabajo para seguir diversos tipos de trabajo, como requisitos del cliente, errores del producto y tareas de desarrollo.|[Seguimiento del trabajo y administrar el flujo de trabajo &#91;redirigido&#93;](http://msdn.microsoft.com/d2d8637d-0ef8-4ca3-874e-a04713344032)|  
  
## <a name="external-resources"></a>Recursos externos  
  
### <a name="guidance"></a>Orientación  
 [Pruebas para entrega continua con Visual Studio 2012 – capítulo 2: Pruebas unitarias: Prueba del interior](http://go.microsoft.com/fwlink/?LinkID=255188)
