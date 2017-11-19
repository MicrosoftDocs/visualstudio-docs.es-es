---
title: "Analizar la calidad del código administrado mediante el análisis de código | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis,managed code
- managed code analyis
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 69cb1ed9c5c8da2ae511d73de45a0567d61236dd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="analyzing-managed-code-quality-by-using-code-analysis"></a>Analizar la calidad del código administrado mediante el análisis de código
Puede usar las herramientas de análisis de código de Visual Studio para detectar posibles problemas del código, como un acceso a datos no seguro, infracciones de uso y problemas de diseño. El análisis de código funciona en aplicaciones de .NET Framework, nativas (C y C++) y de base de datos. Análisis de código para código administrado organiza las reglas en *conjuntos de reglas* que tienen como destino problemas específico de codificación.  
  
## <a name="common-tasks"></a>Tareas comunes  
  
|Tareas comunes|Contenido adicional|  
|------------------|------------------------|  
|**Obtener experiencia práctica:** Conozca los aspectos básicos del análisis de código mediante la corrección de defectos en una sencilla aplicación de .NET Framework.|-   [Tutorial: Analizar código administrado en previsión de defectos de código](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|  
|**Configurar el análisis de código para un proyecto:** las reglas para administrar el código se organizan en conjuntos de reglas orientados a áreas específicas, como seguridad y el diseño. Puede utilizar uno de los conjuntos de regla estándar de Microsoft o crear el suyo propio.|-   [Análisis de código para información general del código administrado](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [Utilizar conjuntos de reglas para agrupar reglas de análisis de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [Suprimir advertencias mediante el atributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|  
|**Ejecutar análisis de código:** puede especificar el análisis de código se ejecute automáticamente cada vez que se crea una configuración de proyecto, y puede ejecutar análisis de código manualmente en un proyecto.|-   [Cómo: habilitar y deshabilitar el análisis de código automático](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [Cómo: ejecutar análisis de código manualmente](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|  
|**Analizar los resultados del análisis de código:** errores y advertencias del análisis de código se muestran en la ventana de análisis de código. Se puede elegir una advertencia o un título de error para mostrar información adicional sobre la advertencia y mostrar y resaltar la línea de código fuente que activó la regla. Se puede elegir el identificador de advertencia para mostrar información detallada en MSDN Library que incluye información y ejemplos de cómo resolver el problema.|-   [Cómo: ver defectos de código administrado](../code-quality/how-to-view-managed-code-defects.md)<br />-   [Análisis de código para las advertencias de código administrado](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [Advertencias de CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [Métodos anónimos y análisis de código](../code-quality/anonymous-methods-and-code-analysis.md)|  
|**Análisis de código se integran con el ciclo de vida de desarrollo:** directivas de protección en [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)] habilitar los equipos de desarrollo para asegurarse de que todo el código protecciones cumplan un conjunto común de estándares de análisis de código. La creación de un elemento de trabajo para la infracción de una regla de análisis de código es un procedimiento simple que se puede realizar en la ventana Lista de errores.|-   [Mejorar la calidad del código con directivas de protección del proyecto de equipo](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [Cómo: sincronizar conjuntos de reglas del proyecto de código con la directiva de comprobación del proyecto de equipo](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [Cómo: crear un elemento de trabajo para defectos de código administrado](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|