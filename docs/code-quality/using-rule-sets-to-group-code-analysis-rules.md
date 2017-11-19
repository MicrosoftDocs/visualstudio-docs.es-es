---
title: "Utilizar conjuntos de reglas para agrupar reglas de análisis de código | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.rulesets.learnmore
helpviewer_keywords: code analysis, rule sets
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 44d64b7371f1b27afaa7796dc42d4b7864d20819
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="using-rule-sets-to-group-code-analysis-rules"></a>Utilizar conjuntos de reglas para agrupar reglas de análisis de código
Al configurar el análisis de código en [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], o [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)], puede elegir entre una lista integrados de Microsoft *conjuntos de reglas*. Un conjunto de reglas es una agrupación lógica de reglas de análisis de código que identifican problemas concretos y condiciones específicas. Por ejemplo, puede aplicar un conjunto de reglas está diseñado para examinar el código para las API disponibles públicamente o puede aplicar un conjunto de reglas que incluya solo las reglas mínimas recomendadas. También puede aplicar un conjunto de reglas que incluye todas las reglas.  
  
 Puede personalizar un conjunto de reglas agregando o eliminando las reglas, o cambiando las reglas que aparezcan en el **lista de errores** ventana como advertencias o errores. Los conjuntos de reglas personalizados pueden satisfacer una necesidad de su entorno de desarrollo determinado. Al personalizar un conjunto de reglas, la página de conjuntos de reglas proporciona herramientas de búsqueda y filtrado para que le sirvan de ayuda en el proceso.  
  
## <a name="common-tasks"></a>Tareas comunes  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Obtener experiencia práctica:** utilice configurar las herramientas de análisis de código para especificar una regla personalizada para buscar y corregir problemas en una sencilla aplicación de .NET Framework.|-   [Tutorial: Configurar y utilizar un conjunto de reglas personalizado](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|  
|**Configurar el análisis de código para un proyecto:** elegir una regla existente establecido para un proyecto, el sitio Web o la solución.|-   [Cómo: configurar el análisis de código para un proyecto de código administrado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [Usar conjuntos de reglas para especificar las reglas de C++ en ejecución](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [Cómo: configurar el análisis de código para una aplicación Web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [Cómo: especificar conjuntos de reglas para varios proyectos en una solución](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|  
|**Personalizar un conjunto de reglas:** especificar reglas que se aplicarán al proyecto.|-   [Crear conjuntos de reglas personalizadas](../code-quality/creating-custom-code-analysis-rule-sets.md)|  
|**Comprender los conjuntos de reglas integradas:** ver las reglas de análisis de código que componen los conjuntos de reglas integradas.|-   [Referencia de conjunto de reglas de análisis de código](../code-quality/code-analysis-rule-set-reference.md)|  
|**Análisis de código se integran con Team Foundation Server:** [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] directivas permiten a los equipos de desarrollo para asegurarse de que todas las protecciones del código cumplen un conjunto común de estándares de análisis de código en el repositorio.|-   [Cómo: sincronizar conjuntos de reglas del proyecto de código con la directiva de comprobación del proyecto de equipo](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|