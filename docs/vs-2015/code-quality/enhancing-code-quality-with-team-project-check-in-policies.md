---
title: Mejorar la calidad del código con directivas de protección del proyecto de equipo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code quality, using check-in policies
- team-based development, enhancing code quality
ms.assetid: 0ab72c33-148a-4a8a-a7bf-046995514c84
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c48a4e9cb68997903eed017637c9f00db88261a5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49299031"
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>Mejorar la calidad del código con directivas de protección de equipo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando se usa el Control de versiones de Team Foundation (TFVC), puede crear directivas de protección para los proyectos de equipo. Aplicación de prácticas que permitan obtener un código mejor y un desarrollo del grupo más eficaz. Las directivas de protección son reglas que se establecen en el nivel del proyecto de equipo y cuya implantación es obligatoria en los equipos de los desarrolladores antes de que el código pueda protegerse.  
  
 Puede especificar las siguientes directivas de protección del proyecto de equipo:  
  
-   **Compilaciones**: requiere que las interrupciones de compilación creadas durante una compilación se corrijan antes de una nueva protección.  
  
-   **Comentarios del conjunto de cambios**: requiere que los usuarios proporcionen comentarios al proteger los cambios.  
  
-   **Análisis de código**: requiere la ejecución del análisis de código antes de llevar a cabo la protección.  
  
-   **Elementos de trabajo**: requiere que uno o varios elementos de trabajo estén asociados a la protección.  
  
> [!IMPORTANT]
>  Para utilizar las directivas de protección, se debe conectar a [!INCLUDE[vststfsLong](../includes/vststfslong-md.md)].  
  
## <a name="common-tasks"></a>Tareas comunes  
  
|Tarea|Contenido adicional|  
|----------|------------------------|  
|**Crear y usar directivas de protección:** puede crear directivas de protección mediante la configuración del proyecto de equipo de [!INCLUDE[esprscc](../includes/esprscc-md.md)].|[Establecer y aplicar pruebas de calidad](http://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|  
|**Crear y usar directivas de protección de análisis de código:** puede elegir un conjunto estándar de reglas de análisis de código o crear un conjunto personalizado.|[Crear y usar directivas de protección del análisis de código](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|  
  
## <a name="related-tasks"></a>Tareas relacionadas  
  
|Tarea|Contenido adicional|  
|----------|------------------------|  
|**Configurar el entorno de desarrollo:** antes de crear o modificar el código, debe configurar los entornos de desarrollo y pruebas usando el código fuente adecuado. Si trabaja con bases de datos, debe tener acceso a su representación sin conexión.|[Configuración de entornos de desarrollo](http://msdn.microsoft.com/en-us/7b686610-d379-4ca0-9608-73ef0e576e3a)|  
|**Usar análisis de código en el proceso de desarrollo:** los miembros del equipo ejecutan análisis de código en sus equipos de desarrollo. En Visual Studio, los desarrolladores configuran y ejecutan series de análisis de código en proyectos de código concretos, ven y analizan los problemas que surgen en las ejecuciones y crean elementos de trabajo para las advertencias.|[Analizar la calidad de la aplicación](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|  
|**Crear y ejecutar pruebas unitarias:** las pruebas unitarias proporcionan a los desarrolladores y evaluadores una forma rápida de buscar errores lógicos en los métodos de clases de proyectos de C#, Visual Basic .NET y C++. Una prueba unitaria se puede crear una vez y ejecutarse cada vez que se cambia el código fuente, a fin de asegurarse de que no se incluye ningún error.|[Haga una prueba unitaria de su código](../test/unit-test-your-code.md)|  
|**Seguimiento de elementos de trabajo y defectos:** puede usar elementos de trabajo para llevar a cabo el seguimiento y la administración del trabajo y la información del proyecto de equipo. Un elemento de trabajo es un registro de base de datos que [!INCLUDE[esprfound](../includes/esprfound-md.md)] usa para seguir la asignación y el progreso del trabajo. Se pueden usar diferentes tipos de elementos de trabajo para seguir diversos tipos de trabajo, como requisitos del cliente, errores del producto y tareas de desarrollo.|[Seguimiento del trabajo y administrar el flujo de trabajo &#91;redirigido&#93;](http://msdn.microsoft.com/en-us/d2d8637d-0ef8-4ca3-874e-a04713344032)|  
  
## <a name="external-resources"></a>Recursos externos  
  
### <a name="guidance"></a>Orientación  
 [Pruebas de entrega continua con Visual Studio 2012. Capítulo 2: Pruebas unitarias: Prueba del interior](http://go.microsoft.com/fwlink/?LinkID=255188)



