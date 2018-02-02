---
title: "Analizar la calidad de la aplicación mediante herramientas de análisis de código | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.codeanalysis.analysisresults
helpviewer_keywords:
- application quality, analyzing
- code analysis
- team-based development, analyzing application quality
ms.assetid: 21680516-ddb5-446d-90d4-19d94f6ec699
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4c07bfffff891e0dbe4ed77ada2682660c74b673
ms.sourcegitcommit: 9a2f937e42305db6e3eaa7aadc235b0ba9aafc83
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/31/2018
---
# <a name="analyzing-application-quality-by-using-code-analysis-tools"></a>Analizar la calidad de la aplicación mediante herramientas de análisis del código
## <a name="in-this-section"></a>En esta sección  
 [Analizar la calidad del código administrado](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)  
 El análisis de Visual Studio Code de código administrado proporciona información sobre los ensamblados administrados como, por ejemplo, las infracciones de las reglas de programación y de diseño estipuladas en las instrucciones de diseño de Microsoft .NET Framework. Los mensajes de advertencia identifican cualquier problema pertinente de programación y diseño y, cuando es posible, proporcionan información sobre la solución del problema.  
  
 [Analizar la calidad de código de C/C++ mediante el análisis de código](../code-quality/analyzing-c-cpp-code-quality-by-using-code-analysis.md)  
 La herramienta Análisis de código de C/C++ proporciona a los desarrolladores información sobre posibles defectos en su código fuente de C/C++. Entre los errores de codificación más comunes detectados por esta herramienta, destacan las saturaciones de búfer, los casos de memoria no inicializada, la desreferenciación del puntero NULL, así como las pérdidas de memoria y recursos.  
  
 [Usar conjuntos de reglas para agrupar reglas de análisis de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)  
 Seleccionar y crear *conjuntos de reglas* para aplicarlas a su proyecto.  
  
 [Errores de la aplicación de análisis de código](../code-quality/code-analysis-application-errors.md)  
 Corrija errores en la funcionalidad de análisis de código.  
  
 [Mejorar la calidad del código con directivas de protección del proyecto de equipo](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)  
 Al usar el control de versiones de Team Foundation (TFVC), pueden crearse directivas de inserción en el repositorio para los proyectos de equipo que apliquen procedimientos que mejoren tanto el código como la eficacia de desarrollo del grupo. Las directivas de protección son reglas que se establecen en el nivel del proyecto de equipo y cuya implantación es obligatoria en los equipos de los desarrolladores antes de que el código pueda protegerse.  
  
### <a name="code-analysis-for-drivers"></a>Análisis de código para controladores  
 Las herramientas de análisis de código pueden ayudar a mejorar la estabilidad y confiabilidad del controlador analizando sistemáticamente el código fuente del controlador.  
  
 [Analizar la calidad del controlador mediante herramientas de análisis de código](http://go.microsoft.com/fwlink/?LinkId=227618)  
 El análisis de código para controladores (Code Analysis for Drivers) es una herramienta de comprobación estática en tiempo de compilación que detecta errores básicos de codificación en programas de C y C++ e incluye un módulo especializado diseñado para detectar errores en el código del controlador en modo kernel (principalmente). El comprobador de controladores estático (Static Driver Verifier, SDV) es una herramienta de comprobación estática que analiza sistemáticamente el código fuente de los controladores en modo kernel de Windows. El SDV determina si el controlador interactúa correctamente con el kernel del sistema operativo de Windows.  
  
 [Análisis de código para las advertencias de controladores](http://go.microsoft.com/fwlink/?LinkId=225920)  
 Describe las advertencias que Code Analysis for Drivers notifica cuando detecta un posible error en el código del controlador.  
  
## <a name="related-tasks"></a>Tareas relacionadas  
 [Medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)  
 Inserte la descripción aquí.  
  
 [Haga una prueba unitaria de su código](../test/unit-test-your-code.md)  
 Inserte la descripción aquí.
