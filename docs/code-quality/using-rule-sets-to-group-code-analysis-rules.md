---
title: "Utilizar conjuntos de reglas para agrupar reglas de an&#225;lisis de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.rulesets.learnmore"
helpviewer_keywords: 
  - "análisis de código, conjuntos de reglas"
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: 36
caps.handback.revision: 36
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Utilizar conjuntos de reglas para agrupar reglas de an&#225;lisis de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Al configurar el análisis de código en [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] o [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)], puede elegir en una lista de *conjuntos de reglas* integrados de Microsoft.  Un conjunto de reglas es una agrupación lógica de reglas de análisis de código que identifican problemas concretos y condiciones específicas.  Por ejemplo, puede aplicar un conjunto de reglas que se diseñan para examinar el código para las API disponibles públicamente o puede aplicar un conjunto de reglas que incluyan solo las reglas mínimas recomendadas.  También puede aplicar un conjunto de reglas que incluya todas las reglas.  
  
 Puede personalizar un conjunto de reglas agregando, eliminando o modificando reglas para que aparezcan en la ventana **Lista de errores** como advertencias o errores.  Los conjuntos de reglas personalizados pueden satisfacer una necesidad de su entorno de desarrollo determinado.  Al personalizar un conjunto de reglas, la página de conjuntos de reglas proporciona herramientas de búsqueda y filtrado para que le sirvan de ayuda en el proceso.  
  
## Tareas comunes  
  
|Tarea|Contenido relacionado|  
|-----------|---------------------------|  
|**Consiga experiencia práctica:** utilice las herramientas de análisis del código para especificar un conjunto de reglas personalizado para buscar y corregir problemas en una aplicación .NET Framework simple.|-   [Tutorial: Configurar y utilizar un conjunto de reglas personalizado](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|  
|**Configure el análisis de código para un proyecto:** elija un conjunto de reglas existente para un proyecto, sitio web o solución.|-   [Cómo: Configurar el análisis de código para un proyecto de código administrado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [Usar conjuntos de reglas para especificar las reglas C\+\+ que se van a ejecutar](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [Cómo: Configurar el análisis de código para una aplicación web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [Cómo: Especificar conjuntos de reglas para varios proyectos de una solución](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|  
|**Personalice un conjunto de reglas:** especifique las reglas que se aplicarán al proyecto.|-   [Crear conjuntos de reglas personalizadas](../code-quality/creating-custom-code-analysis-rule-sets.md)|  
|**Entienda los conjuntos de reglas integrados:** vea las reglas de análisis de código que constituyen los conjuntos de reglas integrados.|-   [Referencia del conjunto de reglas Análisis de código](../code-quality/code-analysis-rule-set-reference.md)|  
|**Integre el análisis de código con Team Foundation Server:** las directivas de protección de [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] permiten a los equipos de desarrolladores asegurarse de que todas las protecciones del código cumplen un conjunto común de normas de análisis de código.|-   [Cómo: Sincronizar conjuntos de reglas del proyecto de código con la directiva de protección del proyecto de equipo](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|