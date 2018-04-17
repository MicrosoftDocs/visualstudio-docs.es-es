---
title: 'Cómo: configurar el análisis de código para una aplicación Web ASP.NET en Visual Studio | Documentos de Microsoft'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 6f0868c825c4e3632a882a044b69e676053800ea
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Cómo: Configurar el análisis de código para una aplicación web ASP.NET

En Visual Studio, puede seleccionar de una lista de análisis de código *conjuntos de reglas* para aplicar a [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicación Web. El conjunto de reglas predeterminado es Reglas mínimas recomendadas de Microsoft. Puede seleccionar otro conjunto de reglas para aplicar al sitio Web.

1. Seleccione el sitio Web en **el Explorador de soluciones**.

2. En el **analizar** menú, haga clic en **configurar análisis de código para el sitio Web**.

3. Si seleccionó la solución y la solución tiene más de un proyecto, seleccione el sistema de operativo de destino y la configuración de compilación de la **configuración** y **plataforma** enumera.

4. Para cada proyecto de la solución, haga clic en el **conjunto de reglas** columna y, a continuación, haga clic en el nombre de la regla configurado para ejecutarse.

5. De forma predeterminada, el análisis de código se ejecuta en todos los proyectos de la solución. Para deshabilitar o habilitar el análisis de código para un proyecto determinado, siga estos pasos:

    1. Haga clic en el nombre del proyecto y, a continuación, haga clic en Propiedades.

    2. Active o desactive el **Habilitar análisis de código** casilla de verificación. También puede ejecutar análisis de código seleccionando **ejecutar análisis de código en el sitio Web** desde el **analizar** menú.

6. En el **ejecutar este conjunto de reglas** lista desplegable lista, siga estos pasos:

    - Seleccione el conjunto de reglas que desea utilizar.

    - Seleccione  **\<examinar >** especificar una regla personalizada existente conjunto que no está en la lista.

    - Definir una [conjunto de reglas personalizado](../code-quality/how-to-create-a-custom-rule-set.md).