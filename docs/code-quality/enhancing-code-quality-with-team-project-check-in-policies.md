---
title: "Mejorar la calidad del c&#243;digo con directivas de protecci&#243;n de equipo | Microsoft Docs"
ms.custom: ""
ms.date: "12/12/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "calidad del código, uso de directivas de protección"
  - "desarrollo basado en equipo, mejora de la calidad del código"
ms.assetid: 0ab72c33-148a-4a8a-a7bf-046995514c84
caps.latest.revision: 25
caps.handback.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Mejorar la calidad del c&#243;digo con directivas de protecci&#243;n de equipo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando se usa el Control de versiones de Team Foundation \(TFVC\), puede crear directivas de protección para los proyectos de equipo. Aplicación de prácticas que permitan obtener un código mejor y un desarrollo del grupo más eficaz. Las directivas de protección son reglas que se establecen en el nivel del proyecto de equipo y cuya implantación es obligatoria en los equipos de los desarrolladores antes de que el código pueda protegerse.  
  
 Puede especificar las siguientes directivas de protección del proyecto de equipo:  
  
-   **Compilaciones**: requiere que las interrupciones de compilación creadas durante una compilación se corrijan antes de una nueva protección.  
  
-   **Comentarios del conjunto de cambios**: requiere que los usuarios proporcionen comentarios al proteger los cambios.  
  
-   **Análisis de código**: requiere la ejecución del análisis de código antes de llevar a cabo la protección.  
  
-   **Elementos de trabajo**: requiere que uno o varios elementos de trabajo estén asociados a la protección.  
  
> [!IMPORTANT]
>  Para utilizar las directivas de protección, se debe conectar a [!INCLUDE[vststfsLong](../code-quality/includes/vststfslong_md.md)].  
  
## Tareas comunes  
  
|Tarea|Contenido adicional|  
|-----------|-------------------------|  
|**Crear y usar directivas de protección:** puede crear directivas de protección mediante la configuración del proyecto de equipo de [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)].|[Establecer y aplicar pruebas de calidad](../Topic/Set%20and%20Enforce%20Quality%20Gates.md)|  
|**Crear y usar directivas de protección de análisis de código:** puede elegir un conjunto estándar de reglas de análisis de código o crear un conjunto personalizado.|[Crear y usar directivas de protección del análisis de código](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|  
  
## Tareas relacionadas  
  
|Tarea|Contenido adicional|  
|-----------|-------------------------|  
|**Configurar el entorno de desarrollo:** antes de crear o modificar el código, debe configurar los entornos de desarrollo y pruebas usando el código fuente adecuado. Si trabaja con bases de datos, debe tener acceso a su representación sin conexión.|[Configuración de entornos de desarrollo](http://msdn.microsoft.com/es-es/7b686610-d379-4ca0-9608-73ef0e576e3a)|  
|**Usar análisis de código en el proceso de desarrollo:** los miembros del equipo ejecutan análisis de código en sus equipos de desarrollo. En Visual Studio, los desarrolladores configuran y ejecutan series de análisis de código en proyectos de código concretos, ven y analizan los problemas que surgen en las ejecuciones y crean elementos de trabajo para las advertencias.|[Analizar la calidad de la aplicación](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|  
|**Crear y ejecutar pruebas unitarias:** las pruebas unitarias proporcionan a los desarrolladores y evaluadores una forma rápida de buscar errores lógicos en los métodos de clases de proyectos de C\#, Visual Basic .NET y C\+\+. Una prueba unitaria se puede crear una vez y ejecutarse cada vez que se cambia el código fuente, a fin de asegurarse de que no se incluye ningún error.|[Haga una prueba unitaria de su código](../test/unit-test-your-code.md)|  
|**Seguimiento de elementos de trabajo y defectos:** puede usar elementos de trabajo para llevar a cabo el seguimiento y la administración del trabajo y la información del proyecto de equipo. Un elemento de trabajo es un registro de base de datos que [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] usa para seguir la asignación y el progreso del trabajo. Se pueden usar diferentes tipos de elementos de trabajo para seguir diversos tipos de trabajo, como requisitos del cliente, errores del producto y tareas de desarrollo.|[Realizar un seguimiento del trabajo y administrar el flujo de trabajo &#91;redirigido&#93;](http://msdn.microsoft.com/es-es/d2d8637d-0ef8-4ca3-874e-a04713344032)|  
  
## Recursos externos  
  
### Orientación  
 [Pruebas de entrega continua con Visual Studio 2012. Capítulo 2: Pruebas unitarias: Prueba del interior](http://go.microsoft.com/fwlink/?LinkID=255188)