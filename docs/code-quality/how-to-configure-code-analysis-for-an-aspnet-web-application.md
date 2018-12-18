---
title: Configurar análisis de código de aplicación Web de ASP.NET
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 8b2776399e776e34126c3c000332aa267682b88f
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065318"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Cómo: Configurar el análisis de código para una aplicación web ASP.NET

En Visual Studio, puede seleccionar entre una lista de análisis de código *conjuntos de reglas* para aplicar a [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicación web. El conjunto de reglas predeterminado es Reglas mínimas recomendadas de Microsoft. Puede seleccionar otro conjunto de reglas para aplicar al sitio web.

1. Seleccione el sitio web en **el Explorador de soluciones**.

2. En el **analizar** menú, haga clic en **configurar análisis de código para el sitio Web**.

3. Si ha seleccionado la solución y la solución tiene más de un proyecto, seleccione el sistema de operativo de configuración y de destino de compilación desde el **configuración** y **plataforma** enumera.

4. Para cada proyecto de la solución, haga clic en el **Pravidel** columna y, a continuación, haga clic en el nombre de la regla de configuración para ejecutar.

5. De forma predeterminada, el análisis de código se ejecuta en todos los proyectos de la solución. Para deshabilitar o habilitar el análisis de código para un proyecto determinado, siga estos pasos:

    1. Haga clic en el nombre del proyecto y, a continuación, haga clic en Propiedades.

    2. Active o desactive el **Habilitar análisis de código** casilla de verificación. También puede ejecutar análisis de código seleccionando **ejecutar análisis de código en el sitio Web** desde el **analizar** menú.

6. En el **ejecutar este conjunto de reglas** desplegable lista, siga estos pasos:

    - Seleccione el conjunto de reglas que desea usar.

    - Seleccione  **\<examinar >** especificar una regla personalizada existente conjunto que no está en la lista.

    - Definir un [conjunto de reglas personalizado](../code-quality/how-to-create-a-custom-rule-set.md).