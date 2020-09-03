---
title: Analizar la calidad de la aplicación mediante herramientas de análisis de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.analysisresults
helpviewer_keywords:
- application quality, analyzing
- code analysis
- team-based development, analyzing application quality
ms.assetid: 21680516-ddb5-446d-90d4-19d94f6ec699
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f8ec0706530cd61653d44533654cf453d25eb42e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75919072"
---
# <a name="analyzing-application-quality-by-using-code-analysis-tools"></a>Analizar la calidad de la aplicación mediante herramientas de análisis del código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En esta sección, [analizar la calidad del código administrado](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) análisis de código de Visual Studio para código administrado proporciona información sobre los ensamblados administrados, como infracciones de las reglas de programación y diseño establecidas en las instrucciones de diseño de Microsoft .NET Framework. Los mensajes de advertencia identifican cualquier problema pertinente de programación y diseño y, cuando es posible, proporcionan información sobre la solución del problema.

 [Analizar la calidad de código de C/C++ mediante el análisis de código](../code-quality/analyzing-c-cpp-code-quality-by-using-code-analysis.md) La herramienta de análisis de código de C/C++ proporciona información a los desarrolladores sobre los posibles defectos en el código fuente de C/C++. Entre los errores de codificación más comunes detectados por esta herramienta, destacan las saturaciones de búfer, los casos de memoria no inicializada, la desreferenciación del puntero NULL, así como las pérdidas de memoria y recursos.

 [Usar conjuntos de reglas para agrupar reglas de análisis de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) Seleccione y cree *conjuntos de reglas* para aplicarlos al proyecto.

 [Errores de aplicación de análisis de código](../code-quality/code-analysis-application-errors.md) Corrija los errores de la funcionalidad de análisis de código.

 [Mejorar la calidad del código con directivas de protección del proyecto de equipo](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md) Al usar Control de versiones de Team Foundation (TFVC), puede crear directivas de protección para los proyectos de equipo que apliquen prácticas que conducen a un mejor código y un desarrollo de grupo más eficaz. Las directivas de protección son reglas que se establecen en el nivel del proyecto de equipo y cuya implantación es obligatoria en los equipos de los desarrolladores antes de que el código pueda protegerse.

### <a name="code-analysis-for-drivers"></a>Análisis de código para controladores
 Las herramientas de análisis de código pueden ayudar a mejorar la estabilidad y confiabilidad del controlador analizando sistemáticamente el código fuente del controlador.

 [Analizar la calidad de los controladores mediante herramientas de análisis de código](/windows-hardware/drivers/devtest/tools-for-verifying-drivers) El análisis de código para controladores es una herramienta de comprobación estática en tiempo de compilación que detecta errores de codificación básicos en programas de C y C++ e incluye un módulo especializado diseñado para detectar errores en el código de controlador de modo kernel (principalmente). El comprobador de controladores estático (Static Driver Verifier, SDV) es una herramienta de comprobación estática que analiza sistemáticamente el código fuente de los controladores en modo kernel de Windows. El SDV determina si el controlador interactúa correctamente con el kernel del sistema operativo de Windows.

 [Advertencias de análisis de código para controladores](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings) Describe las advertencias que el análisis de código para los controladores genera cuando detecta un posible error en el código del controlador.

## <a name="related-tasks"></a>Related Tasks
 [Medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) Inserte aquí la descripción.

 [Prueba unitaria del código](../test/unit-test-your-code.md) Inserte aquí la descripción.
