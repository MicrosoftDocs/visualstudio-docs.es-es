---
title: "Analizar la calidad del c&#243;digo administrado mediante el an&#225;lisis de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "análisis de código, código administrado"
  - "análisis de código administrado"
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 24
---
# Analizar la calidad del c&#243;digo administrado mediante el an&#225;lisis de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede usar las herramientas de análisis de código de Visual Studio para detectar posibles problemas del código, como un acceso a datos no seguro, infracciones de uso y problemas de diseño.  El análisis de código funciona en aplicaciones de .NET Framework, nativas \(C y C\+\+\) y de base de datos.  El análisis de código para el código administrado organiza las reglas en *conjuntos de reglas* orientadas a problemas específicos de codificación.  
  
## Tareas comunes  
  
|Tareas comunes|Contenido adicional|  
|--------------------|-------------------------|  
|**Conseguir experiencia práctica**: obtenga información sobre los fundamentos del análisis de código corrigiendo defectos en una aplicación sencilla de .NET Framework.|-   [Tutorial: Analizar código administrado en previsión de defectos de código](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|  
|**Configurar el análisis de código para un proyecto**: las reglas para el código administrado se organizan en conjuntos de reglas orientados a áreas específicas, como la seguridad y el diseño.  Puede utilizar uno de los conjuntos de regla estándar de Microsoft o crear el suyo propio.|-   [Análisis de código para obtener información general de código administrado](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [Utilizar conjuntos de reglas para agrupar reglas de análisis de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [Suprimir advertencias mediante el atributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|  
|**Ejecutar análisis de código**: puede especificar la ejecución automática del análisis de código cada vez que se compila una configuración de proyecto o ejecutar el análisis de código manualmente en un proyecto.|-   [Cómo: Habilitar y deshabilitar el análisis de código automático](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [Cómo: Ejecutar el análisis de código manualmente](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|  
|**Analizar los resultados del análisis de código**: las advertencias y los errores de análisis de código se muestran en la ventana Análisis de código.  Se puede elegir una advertencia o un título de error para mostrar información adicional sobre la advertencia y mostrar y resaltar la línea de código fuente que activó la regla.  Se puede elegir el identificador de advertencia para mostrar información detallada en MSDN Library que incluye información y ejemplos de cómo resolver el problema.|-   [Cómo: Ver defectos de código administrado](../code-quality/how-to-view-managed-code-defects.md)<br />-   [Análisis de código de las advertencias de código administrado](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [Advertencias de CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [Métodos anónimos y análisis de código](../code-quality/anonymous-methods-and-code-analysis.md)|  
|**Integrar el análisis de código con el ciclo de vida de desarrollo:** las directivas de protección de [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)] permiten a los equipos de desarrolladores asegurarse de que todas las protecciones del código cumplen un conjunto común de normas de análisis de código.  La creación de un elemento de trabajo para la infracción de una regla de análisis de código es un procedimiento simple que se puede realizar en la ventana Lista de errores.|-   [Mejorar la calidad del código con directivas de protección de equipo](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [Cómo: Sincronizar conjuntos de reglas del proyecto de código con la directiva de protección del proyecto de equipo](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [Cómo: Crear un elemento de trabajo para defectos de código administrado](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|