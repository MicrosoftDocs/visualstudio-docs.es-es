---
title: "Analizar la calidad de la aplicaci&#243;n mediante herramientas de an&#225;lisis del c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.analysisresults"
helpviewer_keywords: 
  - "calidad de la aplicación, analizar"
  - "análisis de código"
  - "desarrollo en equipo, analizar la calidad de la aplicación"
ms.assetid: 21680516-ddb5-446d-90d4-19d94f6ec699
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Analizar la calidad de la aplicaci&#243;n mediante herramientas de an&#225;lisis del c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## En esta sección  
 [Analizar la calidad del código administrado](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)  
 El análisis de código administrado de Visual Studio proporciona información sobre los ensamblados administrados como, por ejemplo, las infracciones de las reglas de programación y de diseño estipuladas en las instrucciones de diseño de Microsoft .NET Framework.  Los mensajes de advertencia identifican cualquier problema pertinente de programación y diseño y, cuando es posible, proporcionan información sobre la solución del problema.  
  
 [Analizar la calidad del código C\/C\+\+](../code-quality/analyzing-c-cpp-code-quality-by-using-code-analysis.md)  
 La herramienta Análisis de código de C\/C\+\+ proporciona a los desarrolladores información sobre posibles defectos en su código fuente de C\/C\+\+.  Entre los errores de codificación más comunes detectados por esta herramienta, destacan las saturaciones de búfer, los casos de memoria no inicializada, la desreferenciación del puntero NULL, así como las pérdidas de memoria y recursos.  
  
 [Utilizar conjuntos de reglas para agrupar reglas de análisis de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)  
 Seleccione y cree *conjuntos de reglas* para aplicarlos al proyecto.  
  
 [Errores de la aplicación de análisis de código](../code-quality/code-analysis-application-errors.md)  
 Corrija errores en la funcionalidad de análisis de código.  
  
 [Mejorar la calidad del código con directivas de protección de equipo](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)  
 Al usar el control de versiones de Team Foundation \(TFVC\), pueden crearse directivas de protección para los proyectos de equipo que apliquen procedimientos que mejoren tanto el código como la eficacia de desarrollo del grupo.  Las directivas de protección son reglas que se establecen en el nivel del proyecto de equipo y cuya implantación es obligatoria en los equipos de los desarrolladores antes de que el código pueda protegerse.  
  
### Análisis de código para controladores  
 Las herramientas de análisis de código pueden ayudar a mejorar la estabilidad y confiabilidad del controlador analizando sistemáticamente el código fuente del controlador.  
  
 [Analizar la calidad del controlador mediante herramientas de análisis del código](http://go.microsoft.com/fwlink/?LinkId=227618)  
 El análisis de código para controladores \(Code Analysis for Drivers\) es una herramienta de comprobación estática en tiempo de compilación que detecta errores básicos de codificación en programas de C y C\+\+ e incluye un módulo especializado diseñado para detectar errores en el código del controlador en modo kernel \(principalmente\).  El comprobador de controladores estático \(Static Driver Verifier, SDV\) es una herramienta de comprobación estática que analiza sistemáticamente el código fuente de los controladores en modo kernel de Windows.  El SDV determina si el controlador interactúa correctamente con el kernel del sistema operativo de Windows.  
  
 [Advertencias de análisis de código para controladores](http://go.microsoft.com/fwlink/?LinkId=225920)  
 Describe las advertencias que Code Analysis for Drivers notifica cuando detecta un posible error en el código del controlador.  
  
## Tareas relacionadas  
 [Medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)  
 Inserte la descripción aquí.  
  
 [Haga una prueba unitaria de su código](../test/unit-test-your-code.md)  
 Inserte la descripción aquí.