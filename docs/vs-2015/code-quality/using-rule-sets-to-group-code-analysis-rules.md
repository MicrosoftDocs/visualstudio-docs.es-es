---
title: Usar conjuntos de reglas para agrupar reglas de análisis de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 30bd2e53531d9abc7d27adba05c3b724c88d61c3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603477"
---
# <a name="using-rule-sets-to-group-code-analysis-rules"></a>Utilizar conjuntos de reglas para agrupar reglas de análisis de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al configurar el análisis de código en [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] o [!INCLUDE[vsPro](../includes/vspro-md.md)], puede elegir en una lista de *conjuntos de reglas*integrados de Microsoft. Un conjunto de reglas es una agrupación lógica de reglas de análisis de código que identifican problemas concretos y condiciones específicas. Por ejemplo, puede aplicar un conjunto de reglas diseñado para examinar el código de las API disponibles públicamente o puede aplicar un conjunto de reglas que incluya solo las reglas mínimas recomendadas. También puede aplicar un conjunto de reglas que incluya todas las reglas.

 Puede personalizar un conjunto de reglas agregando o eliminando reglas, o cambiando reglas para que aparezcan en la ventana de **lista de errores** como advertencias o errores. Los conjuntos de reglas personalizados pueden satisfacer una necesidad de su entorno de desarrollo determinado. Al personalizar un conjunto de reglas, la página de conjuntos de reglas proporciona herramientas de búsqueda y filtrado para que le sirvan de ayuda en el proceso.

## <a name="common-tasks"></a>Tareas comunes

|Tarea|Contenido relacionado|
|----------|---------------------|
|**Obtener prácticas recomendadas:** Use las herramientas de análisis de código para especificar un conjunto de reglas personalizado para buscar y corregir problemas en una aplicación de .NET Framework simple.|-   [Tutorial: configurar y usar un conjunto de reglas personalizado](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|
|**Configurar el análisis de código para un proyecto:** Elija un conjunto de reglas existente para un proyecto, sitio web o solución.|-   [Cómo: configurar el análisis de código para un proyecto de código administrado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [usar conjuntos de reglas para especificar C++ las reglas que se van a ejecutar](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [Cómo: configurar el análisis de código para una aplicación Web ASP.net](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [Cómo: especificar conjuntos de reglas para varios proyectos de una solución](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|
|**Personalizar un conjunto de reglas:** Especifique las reglas que se van a aplicar al proyecto.|-   [crear conjuntos de reglas personalizadas](../code-quality/creating-custom-code-analysis-rule-sets.md)|
|**Comprender los conjuntos de reglas integrados:** Ver las reglas de análisis de código que componen los conjuntos de reglas integrados.|[referencia de conjunto de reglas de análisis de código](../code-quality/code-analysis-rule-set-reference.md) -   |
|**Integrar el análisis de código con Team Foundation Server:** [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] las directivas de inserción en el repositorio permiten a los equipos de desarrollo asegurarse de que todas las protecciones del código cumplen un conjunto común de normas de análisis de código.|-   [Cómo: sincronizar conjuntos de reglas del proyecto de código con la Directiva de inserción en el repositorio del proyecto de equipo](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|
